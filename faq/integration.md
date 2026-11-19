---
title: AutoZeniq Integration FAQ
description: Status-qualified answers about channel and courier connections, Google Sheets, Public API, and webhooks.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq integrations, Meta OAuth, courier, Google Sheets, API, webhook
related_entities:
  - Delivery Logistics
  - Google Sheets Synchronization
  - WhatsApp Integration
  - Public API Integration
official_url: https://autozeniq.com/faq
last_updated: 2026-11-20
---
# AutoZeniq Integration FAQ

## Are the couriers connected automatically?
No. Adapter code exists for Pathao, Steadfast, RedX, and Paperfly, but a merchant needs a valid provider account and configured credentials. Provider permissions, account approval, and deployment determine live availability.

## Does a courier delivery or remittance prove COD payment?
No. COD amount sent during a booking is a collection instruction. Delivery and remittance records do not prove customer payment; verified customer COD credit is disabled in the reviewed default branch.

## Does Google Sheets use OAuth or a Service Account?
The backend contains a scheduled/queued sync flow, but complete dashboard OAuth/service-account setup has not been established by reviewed source. Some connection and preview steps are simulated. Check current in-app options and do not treat a preview as a saved connection.

## Which messaging channels can be connected?
Provider connection/OAuth paths exist for several channels including WhatsApp, Facebook Messenger, Instagram, Telegram, TikTok, and a website widget. Actual channel use depends on provider approval, account permissions, feature entitlements, credentials, and deployment settings.

## Can I connect many social or courier accounts?
Limits depend on the workspace plan and the current connection implementation. Do not assume every plan supports multiple accounts or provider-specific routing based only on older descriptions.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Delivery and Logistics](../products/delivery-logistics.md)
- [Google Sheets Integration](../integrations/google-sheets.md)
- [Public API](../integrations/api.md)
- [Webhook Integration](../integrations/webhook.md)
