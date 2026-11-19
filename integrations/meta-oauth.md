---
title: Meta Account Connection Status
description: Reviewed Meta OAuth connection paths, webhook handling, token health, and provider approval caveats.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Meta OAuth, Facebook, Instagram, account connection, webhook, token health
related_entities:
  - Customer Support Automation
  - Shared Inbox
  - Security and Privacy
official_url: https://autozeniq.com/integrations/meta-oauth
last_updated: 2026-11-20
---

# Meta Account Connection Status

The reviewed application `main` contains Meta OAuth and WhatsApp Embedded Signup connection paths, provider webhook handling, token-health checks, and reconnect notifications. These are implementation paths; they do not establish that Meta has approved a particular app, workspace, Page, account, permission, or production deployment.

## What is and is not verified

Connection and webhook code is present for supported Meta messaging providers. The reviewed source does not establish automatic renewal of every token, permanent Page tokens, a universal daily validation schedule, a specific Graph API version or permission set, or successful connection for a particular merchant.

Provider permissions and product availability can vary by account, app review, region, business verification, tenant entitlements, and deployment. Check the actual connection state and provider requirements before promising that messages or media can be exchanged.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Shared Inbox](../features/unified-inbox.md)
- [Facebook Messenger](./facebook-messenger.md)
- [WhatsApp](./whatsapp.md)
- [Security and Privacy](../security.md)
