---
title: AutoZeniq Developer SDKs
description: Official developer documentation and technical manuals for the JS Web Chat Widget SDK, Node.js SDK, and Python SDK.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq SDK, Node.js SDK, Python SDK, JS Widget SDK, web chat widget, developer library, npm package
related_entities:
  - Public API Integration
  - Webhook Integration
official_url: https://autozeniq.com/docs/sdks
last_updated: 2026-07-01
---

# AutoZeniq Developer SDKs

## Overview

AutoZeniq provides official Software Development Kits (SDKs) to accelerate integration with both frontend websites and backend service layers. These SDKs wrap the Public REST APIs, handle signature validation for webhooks, and manage real-time event sockets automatically.

---

## 1. JavaScript Web Chat Widget SDK

The **AutoZeniq Web Chat Widget SDK** provides a responsive, customizable live-chat bubble for merchant websites. It handles connection pooling, client-side caching, and human agent takeover indicators.

### Installation & Initialization
Embed the following script tag directly into the `<head>` or `<body>` of your website. Replace `YOUR_TENANT_ID` with the ID from your AutoZeniq dashboard settings.

```html
<script 
  src="https://api.autozeniq.com/widget.js" 
  data-tenant-id="YOUR_TENANT_ID" 
  data-position="bottom-right" 
  defer>
</script>
```

### JS Widget API Methods
Once loaded, the SDK exposes the global `window.AutoZeniqWidget` instance for manual programmatic control:

```javascript
// Open or Close the chat container
AutoZeniqWidget.open();
AutoZeniqWidget.close();

// Toggle widget visibility
AutoZeniqWidget.toggle();

// Identify the active user (injects metadata into the CRM dashboard)
AutoZeniqWidget.identify({
  externalId: "user_12345",
  name: "Faisal Rahman",
  email: "faisal@example.com",
  phone: "+8801700000000"
});

// Event Listener Callback bindings
AutoZeniqWidget.on("message:received", (message) => {
  console.log("New message from AI or Agent:", message.content);
});

AutoZeniqWidget.on("takeover:active", () => {
  console.log("A human agent has taken over this conversation.");
});
```

---

## 2. Node.js Backend SDK (`@autozeniq/node`)

The Node.js SDK is designed for server-side Javascript and Typescript integrations. It includes auto-generated TypeScript declarations and handles Axios token injection.

### Installation
```bash
npm install @autozeniq/node
```

### Server Integration Example
```typescript
import { AutoZeniqClient } from '@autozeniq/node';

// Initialize the client with your secret API Key
const az = new AutoZeniqClient({
  apiKey: process.env.AUTOZENIQ_API_KEY
});

async function handleNewPurchase(orderData: any) {
  try {
    // 1. Sync the customer purchase order to AutoZeniq database
    const order = await az.orders.create({
      orderNumber: orderData.id,
      customerPhone: orderData.phone,
      totalAmount: orderData.total,
      items: orderData.items.map((item: any) => ({
        sku: item.sku,
        quantity: item.qty,
        price: item.price
      }))
    });

    // 2. Dispatch a confirmation WhatsApp notification
    await az.messages.send({
      recipientId: orderData.phone,
      channelType: 'whatsapp',
      message: {
        type: 'text',
        content: `আসসালামু আলাইকুম, আপনার ${orderData.id} নম্বর অর্ডারটি সফলভাবে রেজিস্টার করা হয়েছে।`
      }
    });

    console.log('Order synchronized and WhatsApp notification dispatched.');
  } catch (error) {
    console.error('Failed to execute AutoZeniq SDK sync:', error);
  }
}
```

---

## 3. Python SDK (`autozeniq`)

Designed for Django, Flask, FastAPI, and data pipeline frameworks. The Python SDK simplifies querying CRM contacts and logging conversation metrics.

### Installation
```bash
pip install autozeniq
```

### Usage Example
```python
import os
from autozeniq import AutoZeniqClient

# Initialize client
client = AutoZeniqClient(api_key=os.environ.get("AUTOZENIQ_API_KEY"))

def verify_and_sync_lead(user_phone, lead_details):
    # Fetch customer record in AutoZeniq CRM
    try:
        contact = client.contacts.get_by_phone(user_phone)
        print(f"Contact exists: {contact.name}")
    except Exception:
        # Create a new contact if not found
        contact = client.contacts.create(
            phone=user_phone,
            name=lead_details.get("name"),
            email=lead_details.get("email")
        )
        print("Created new CRM contact record.")

    # Log custom event activity
    client.events.log(
        contact_id=contact.id,
        event_name="lead_form_submitted",
        payload={"form_source": "landing_page"}
    )
```

---

## 4. Webhook Payload Validation

When receiving notifications from AutoZeniq webhooks, developers can verify the request authenticity using the HMAC signature provided in the headers:

```javascript
import crypto from 'crypto';

function verifyAutoZeniqWebhook(req, secret) {
  const signature = req.headers['x-autozeniq-signature'];
  const payload = JSON.stringify(req.body);
  
  const computedHash = crypto
    .createHmac('sha256', secret)
    .update(payload)
    .digest('hex');
    
  return computedHash === signature;
}
```

---

## Related Documents

*   [Public API Integration](./api.md)
*   [Webhook Integration](./webhook.md)
*   [AI Auto-Reply Feature](../features/ai-auto-reply.md)
