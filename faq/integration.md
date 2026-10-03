---
title: AutoZeniq Integration & Channels FAQ
description: Frequently asked questions about connecting messaging channels, courier networks, and Google Sheets to AutoZeniq.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq integration faq, Meta OAuth, Pathao API, Steadfast courier, Google Sheets API, courier integration
related_entities:
  - Delivery Logistics
  - Google Sheets Synchronization
  - WhatsApp Integration
  - Facebook Messenger Integration
official_url: https://autozeniq.com/faq
last_updated: 2026-10-03
---

# AutoZeniq Integration & Channels FAQ

This document covers common questions regarding connecting, authorizing, and managing social channels, courier networks, and spreadsheet databases on the AutoZeniq platform.

---

## FAQ

### Q: How do I connect Pathao Courier to AutoZeniq?
**A:** In the AutoZeniq dashboard under **Settings > Integrations > Delivery > Pathao**, enter your Pathao Developer Client ID, Client Secret, Username, and Password. AutoZeniq exchanges these credentials for an auto-renewing OAuth bearer token, retrieves your pickup store IDs, and enables automatic consignment creation.

### Q: How does Steadfast Courier connect to AutoZeniq?
**A:** Under **Settings > Integrations > Delivery > Steadfast**, enter your Steadfast API Key and Secret Key found in your Steadfast Merchant Portal. All communications are secured using header-based authentication, enabling instant parcel dispatch and automated tracking updates.

### Q: What is the difference between connecting Google Sheets via OAuth vs. Service Account?
**A:**
*   **One-Click Google OAuth**: Best for small merchants. Click "Connect with Google", approve read access, and select your sheet.
*   **Google Service Account**: Recommended for enterprise teams. Upload a Google Cloud Service Account JSON key and share the Google Sheet with the generated service account email.

### Q: How does the Meta OAuth integration work?
**A:** AutoZeniq uses an official Meta Business Login popup dialog. Merchants click "Connect Meta", approve page permissions in the secure popup, and the system automatically exchanges the code for a 60-day long-lived token, subscribes the page to webhooks, and starts a daily token validation cron worker.

### Q: Can I connect multiple Facebook pages or couriers to a single workspace?
**A:** Yes. Depending on your subscription plan, multiple Facebook Pages, Instagram profiles, and multiple courier accounts (e.g. Pathao for Dhaka, Steadfast for outside Dhaka) can be connected simultaneously.

---

## Related Documents

* [Pathao Courier Integration](../integrations/pathao-courier.md)
* [Steadfast Courier Integration](../integrations/steadfast-courier.md)
* [Google Sheets Integration Guide](../integrations/google-sheets.md)
* [Meta Platform Native OAuth](../integrations/meta-oauth.md)
