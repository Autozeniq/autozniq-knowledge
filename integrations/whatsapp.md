---
title: WhatsApp Business API Integration
description: Technical details, Meta Embedded Signup flows, and message delivery schemas for the WhatsApp Business API on AutoZeniq.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq WhatsApp, WhatsApp Business API, WABA, Embedded Signup, webhooks, Meta OAuth
related_entities:
  - Customer Support Automation
  - Facebook Integration
official_url: https://autozeniq.com/integrations/whatsapp
last_updated: 2026-06-24
---

# [WhatsApp Business API Integration](https://autozeniq.com/integrations/whatsapp)

## Overview

AutoZeniq integrates with Meta's official **[WhatsApp Business API](https://autozeniq.com/integrations/whatsapp)**. This allows businesses to send and receive text, media, and template messages from a verified WhatsApp Business Account (WABA) directly through the AutoZeniq unified inbox and AI routing engine.

---

## Technical Architecture

The integration leverages Meta's secure Embedded Signup and Webhook systems:

### Simple Explanation
To connect a WhatsApp number, the business owner clicks "Connect WhatsApp" in their AutoZeniq dashboard. A secure Meta window opens, asking them to log in to Facebook and select their WhatsApp Business Account. After verifying their phone number via SMS or voice call, the connection is complete. Messages sent to that number will instantly show up in their AutoZeniq inbox.

### Technical Explanation
1.  **Meta Embedded Signup**: Operates using Meta's Cloud API Embedded Signup SDK. The frontend opens a popup window requesting access to user profiles, billing accounts, and WABA resources. Upon completion, Meta returns a short-lived user access token.
2.  **System Token Exchange**: The NestJS backend exchanges the short-lived token for a long-lived access token, encrypts it at rest using `AES-256-GCM`, and links it to the `tenant_id`.
3.  **Token Validation Cron**: A daily cron worker verifies each tenant's token health against Meta's `/debug_token` endpoint, checking expiration countdowns and triggering email alerts if re-authentication is required.
4.  **Webhook Gateway**: Incoming messages are received at `/api/integrations/whatsapp/webhook`. The system validates Meta's `X-Hub-Signature-256` header (calculated using HMAC-SHA256 and the Meta App Secret) to verify payload authenticity before passing messages to the database queue.

---

## Core Features

*   **Embedded Signup Popup**: One-click Meta popup flow that eliminates manual token copy-pasting.
*   **Token Health Dashboard**: Displays the token status and refresh countdown on connection cards in the Integrations UI.
*   **Meta Template Message Delivery**: Sends approved template notifications to customers outside the standard 24-hour conversational window.
*   **Media Handling**: Supports incoming and outgoing media files (images, audio, PDF documents, location pins).
*   **Interactive List/Buttons Support**: Delivers structured messaging lists and quick-reply buttons.

---

## Benefits

*   **Official API Credibility**: Enables businesses to secure the green verification badge on WhatsApp.
*   **No App Downtime**: Uses Meta's Cloud API hosting, avoiding message drops caused by offline phone apps.
*   **Scale**: Supports high-volume incoming message rates through Redis messaging queues (`BullMQ`).

---

## Use Cases

*   **Conversational Orders**: Allowing customers to view catalogs, select items, and confirm purchases on WhatsApp.
*   **Automated Shipping Notifications**: Triggering template messages containing tracking details when an order state updates.
*   **24/7 Support Channel**: Utilizing RAG knowledge bases to answer product questions on WhatsApp automatically.

---

## FAQ

### Q: Can I connect a number currently active on the standard WhatsApp mobile app?
**A:** No. Meta requires that a phone number be deleted from standard WhatsApp apps before it can be registered with the WhatsApp Business API.

### Q: Are there messaging fees for using the WhatsApp API?
**A:** Yes. Meta charges per conversation based on the conversation category (Utility, Marketing, Authentication, or Service). Details are managed in the Meta Business Portfolio billing section.

---

## Related Documents

*   [Facebook Integration](./facebook.md)
*   [API Integration](./api.md)
*   [Product Overview](../products/overview.md)
