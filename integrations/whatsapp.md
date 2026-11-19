---
title: WhatsApp Business Connection
description: Status-qualified overview of WhatsApp Embedded Signup and webhook paths with account, approval, and message-feature caveats.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq WhatsApp, WhatsApp Business, Embedded Signup, webhook, account connection
related_entities:
  - Customer Support Workflows
  - Meta Account Connection
  - Shared Inbox
official_url: https://autozeniq.com/integrations/whatsapp
last_updated: 2026-11-20
---

# WhatsApp Business Connection

The reviewed application `main` contains a WhatsApp Embedded Signup connection path, provider webhook handling, token-health checks, and reconnect notifications. A code path is not proof that a particular WhatsApp Business Account (WABA), phone number, or tenant is connected, approved, or live.

## Availability and message features

Use depends on Meta business verification and app permissions, WABA and phone-number status, workspace configuration, entitlements, credentials, provider rules, and deployment. The reviewed source does not establish every template, interactive message, location, media type, automatic order notification, or delivery-window behavior. Verify the relevant provider capability and connection before promising it.

The shared inbox supports conversation history, human replies, assignment, AI pause/takeover/resume, and selected real-time updates. AI Copilot suggestions are drafts. Guarded auto-reply behavior depends on channel and workspace configuration.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Meta Account Connection](./meta-oauth.md)
- [Shared Inbox](../features/unified-inbox.md)
- [Customer Support Workflows](../features/customer-support.md)
