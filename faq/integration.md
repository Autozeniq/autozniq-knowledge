---
title: AutoZeniq Integration & Channels FAQ
description: Frequently asked questions about connecting messaging channels (WhatsApp, Facebook Page, Messenger, Telegram) to AutoZeniq.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq integration faq, Meta Graph API permissions, WhatsApp Business verification, webhook setup, channel tokens
related_entities:
  - WhatsApp Integration
  - Facebook Messenger Integration
  - Telegram Integration
official_url: https://autozeniq.com/faq
last_updated: 2026-06-24
---

# AutoZeniq Integration & Channels FAQ

This document covers common questions regarding connecting, authorizing, and managing social media and messaging channels on the AutoZeniq platform.

---

## FAQ

### Q: What Meta Graph API permissions are required for Facebook Page Comment automation?
**A:** Setting up comments automation requires a Meta Page Access Token generated through Facebook Login with the following permissions:
*   `pages_show_list`
*   `pages_read_engagement`
*   `pages_manage_metadata`
*   `pages_manage_engagement`

### Q: Do I need a verified Facebook Business Manager to use the WhatsApp integration?
**A:** While you can test WhatsApp automation in sandbox environments using developer numbers, live production deployment requires a verified Meta Business Manager account and a registered phone number associated with the WhatsApp Business Cloud API.

### Q: How do I bind a Telegram bot to my AutoZeniq channel?
**A:** Generate an HTTP API Token by messaging the official Telegram `@BotFather`. Copy the generated token, navigate to **Settings > Integrations > Telegram** in your AutoZeniq dashboard, and save the token. AutoZeniq automatically communicates with Telegram's API to set the active webhook endpoint URL.

### Q: What happens if Meta Graph API endpoints rate limit the platform?
**A:** Meta Graph API requests are bound by Page-level rate limits. AutoZeniq implements token-bucket queueing on outgoing message workers. If a request is throttled with a `103` rate limit error, the worker schedules a retry after the delay specified in the `x-business-use-case-usage` or `Retry-After` headers.

### Q: Can I connect multiple Facebook pages to a single client tenant account?
**A:** Yes. Under **Settings > Integrations**, you can authenticate via Meta OAuth and select one or more Pages to subscribe to. Each selected Page functions as a distinct channel within the unified inbox of the same client account.

---

## Related Documents

*   [Facebook Messenger Integration](../integrations/facebook-messenger.md)
*   [WhatsApp Integration](../integrations/whatsapp.md)
*   [Telegram Integration](../integrations/telegram.md)
