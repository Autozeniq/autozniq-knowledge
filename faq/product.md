---
title: AutoZeniq Product & Features FAQ
description: Frequently asked questions about product features, storefront builder, order state machine, courier dispatching, and agent controls in AutoZeniq.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq product faq, storefront builder, courier booking, quick order drawer, google sheets sync, OMS state machine
related_entities:
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
  - Google Sheets Synchronization
official_url: https://autozeniq.com/faq
last_updated: 2026-10-03
---

# AutoZeniq Product & Features FAQ

This guide answers questions about utilizing the AutoZeniq dashboard features, designing online stores, managing orders, booking couriers, and synchronizing spreadsheets.

---

## FAQ

### Q: How does the Storefront Builder work?
**A:** Located under **Store Builder** in the dashboard, the visual drag-and-drop editor allows merchants to customize page layouts (Home, Catalog, Product Details, Cart, Checkout) across desktop and mobile viewports. Stores are served via an optimized Next.js 14 runtime under `store.autozeniq.com` or custom merchant CNAME domains.

### Q: What is the In-Chat Quick Order Drawer?
**A:** While conversing with a customer in the Omnichannel Inbox, support agents or sales reps can slide open the Quick Order drawer. Staff can search the live catalog, pick sizes/colors, apply custom shipping discounts, and confirm orders directly into the OMS without switching tabs.

### Q: How does AutoZeniq connect to regional couriers?
**A:** AutoZeniq's `CourierRegistry` supports **Pathao**, **Steadfast**, **RedX**, and **Paperfly**. Merchants configure their API keys or OAuth credentials once in Settings. When an order is confirmed, the system can automatically book a consignment, generate a tracking code, and notify the customer via SMS or WhatsApp.

### Q: How does the Google Sheets integration stay up to date?
**A:** The Google Sheets Sync service polls connected spreadsheets on scheduled intervals (hourly or daily) or upon clicking "Sync Now". The service uses smart auto-mapping for English and Bengali headers (`পণ্যের নাম`, `দাম`, `স্টক`) and processes updates asynchronously via BullMQ.

### Q: What happens if an order is cancelled?
**A:** The deterministic state machine validates the cancellation, updates the order status to `CANCELLED`, and executes an atomic database transaction to return the reserved product quantities back to available stock.

---

## Related Documents

* [Storefront Builder](../products/store-builder.md)
* [Order Management System](../products/order-management.md)
* [Delivery & Logistics Automation](../products/delivery-logistics.md)
* [Google Sheets Synchronization](../../features/google-sheets-sync.md)
