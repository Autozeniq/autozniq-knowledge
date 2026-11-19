---
title: Telegram Bot Connection
description: Status-qualified overview of Telegram integration paths and workspace/provider availability limits.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq Telegram, Telegram Bot, connection, webhook, shared inbox
related_entities:
  - Customer Support Workflows
  - Shared Inbox
official_url: https://autozeniq.com/integrations/telegram
last_updated: 2026-11-20
---

# Telegram Bot Connection

The reviewed application `main` contains a Telegram provider-connection path and webhook handling. This does not establish that a bot token has been saved, the bot is connected for a specific workspace, or the integration is operating in production.

## Availability and limits

Use depends on a valid provider configuration, tenant permissions and entitlements, and deployment. The reviewed source does not establish support for every Telegram message type, inline keyboards, media format, webhook lifecycle behavior, rate-limit policy, or automatic AI reply. Confirm the actual connected bot and message path before making a channel-specific claim.

Where available, agents use the shared inbox's conversation history, human replies, assignment, and AI controls. AI Copilot suggestions are drafts, and automatic replies depend on configuration.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Shared Inbox](../features/unified-inbox.md)
- [Customer Support Workflows](../features/customer-support.md)
- [AI Agent](../products/ai-agent.md)
