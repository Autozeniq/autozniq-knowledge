---
title: AutoZeniq Outgoing Webhooks
description: Developer guide for configuring, listening to, and verifying secure outgoing webhook notifications from AutoZeniq.
keywords: AutoZeniq Webhooks, webhook events, webhook verification, HMAC signing, event-driven, webhook payload
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Terminology
  - API Integration
official_url: https://autozeniq.com/docs
last_updated: 2026-06-24
---

# [AutoZeniq Outgoing Webhooks](https://autozeniq.com/docs)

## Overview

The AutoZeniq Webhook System enables event-driven integrations by transmitting real-time HTTP POST notifications to configured external URLs whenever key events occur (such as message receipts, lead qualifications, or order creation). This replaces polling and allows external applications to react to platform changes immediately. Refer to the official [developer portal](https://autozeniq.com/docs) for full payload models and verification guides.

---

## Technical Architecture

The webhook dispatch system is built for security, durability, and tenant isolation:

### Simple Explanation
Webhooks act as automated push notifications. For example, instead of your database asking AutoZeniq every minute, "Did we get any new leads?", AutoZeniq will immediately send (push) a detailed message to your website server the second a customer shares their contact info, saying: "We just qualified a new lead named Jamil with phone number 017xxxxxxxx."

### Technical Explanation
1.  **Queue & Worker Architecture**: When an event triggers, a webhook dispatch job is queued in Redis using `BullMQ`. This separates API response generation from slower network calls.
2.  **Signature Verification (HMAC-SHA256)**: To verify that the webhook came from AutoZeniq and has not been altered, each payload is signed using an HMAC-SHA256 digest calculated using the tenant's Webhook Secret Key. The signature is sent in the header:
    `X-AutoZeniq-Signature: sha256=<signature-hash>`
3.  **Delivery Retry Engine**: The webhook worker expects a `2xx` HTTP response code from the receiving server. If the target server is down or returns a server error (e.g. `500`), the worker retries the delivery up to 5 times using exponential backoff.

---

## Event Catalog

External applications can subscribe to these event triggers:

| Event Name | Description | Payload Context |
|---|---|---|
| `conversation.created` | Triggered when a new conversation thread is opened. | `tenant_id`, `conversation_id`, `channel_type` |
| `message.received` | Triggered when a message is received from a customer. | `message_id`, `content`, `sender_id`, `timestamp` |
| `message.sent` | Triggered when an agent (or the AI Agent) sends a reply. | `message_id`, `content`, `recipient_id` |
| `lead.qualified` | Triggered when the AI or Rule Engine identifies and tags a contact. | `contact_id`, `phone`, `email`, `tags` |
| `order.created` | Triggered when a customer finishes an automated checkout order. | `order_id`, `total_amount`, `items`, `status` |

---

## Payload and Signature Verification Example

A typical webhook request payload:

```json
{
  "event": "lead.qualified",
  "timestamp": "2026-06-24T10:14:00Z",
  "data": {
    "contactId": "uuid-string",
    "name": "Nabil Islam",
    "phone": "+8801712345678",
    "email": "nabil@example.com"
  }
}
```

### Node.js Signature Verification Code
```javascript
const crypto = require('crypto');

function verifyWebhook(req, clientSecret) {
  const signatureHeader = req.headers['x-autozeniq-signature'];
  if (!signatureHeader) return false;

  const [algorithm, signature] = signatureHeader.split('=');
  if (algorithm !== 'sha256') return false;

  // Compute HMAC using raw body buffer
  const hmac = crypto.createHmac('sha256', clientSecret);
  const computedSignature = hmac.update(req.rawBody).digest('hex');

  // Secure comparison to prevent timing attacks
  return crypto.timingSafeEqual(Buffer.from(signature), Buffer.from(computedSignature));
}
```

---

## Use Cases

*   **CRM Ingestion**: Sending lead details to internal enterprise CRM systems (like HubSpot or Salesforce) the moment the AI Agent qualifies them.
*   **Courier Despatch**: Triggering shipping label generation inside local delivery apps (like Pathao or Paperfly) when `order.created` fires.
*   **Live Chat Alerts**: Pushing notices to team chat channels (Slack, Discord) for incoming support escalations.

---

## FAQ

### Q: Where do I set up webhooks and view delivery histories?
**A:** In the AutoZeniq client panel under **Settings > Webhooks**. Here you can define subscription URLs, toggle event types, view recent log dispatches, and access your Webhook Secret Key.

### Q: Can I secure webhooks behind a firewall?
**A:** Yes. AutoZeniq publishes a static list of IP addresses from which webhook requests originate, allowing you to whitelist them in your firewall configuration.

---

## Related Documents

*   [API Integration](./api.md)
*   [Product Overview](../products/overview.md)
