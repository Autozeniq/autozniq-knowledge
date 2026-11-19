---
title: Facebook Messenger Connection
description: Status-qualified overview of Messenger connection and webhook paths with provider and message-type caveats.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq Messenger, Facebook Messenger, Meta OAuth, connection, webhook
related_entities:
  - Facebook Integration
  - Customer Support Workflows
  - Shared Inbox
official_url: https://autozeniq.com/integrations/facebook-messenger
last_updated: 2026-11-20
---

# Facebook Messenger Connection

The reviewed application `main` contains Meta account-connection and provider-webhook paths for supported messaging channels, including Facebook Messenger. If a workspace has a valid, approved provider connection and the channel is enabled, conversation paths can feed into the shared inbox. Source code alone does not confirm that a particular Page is connected or that the integration is operating in production.

## Availability and message types

Meta app review, Page permissions, workspace configuration, entitlements, credentials, deployment, and provider rules affect availability. The reviewed source does not establish universal read-receipt indicators, public comment replies, private comment follow-ups, carousel or template delivery, or support for every attachment type. Verify the exact message type in the connected account before describing it as supported.

Agents can use the shared inbox's verified conversation features, including message history, human replies, assignment, and configured AI controls. AI Copilot suggestions are drafts; automatic reply paths depend on configuration.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Meta Account Connection](./meta-oauth.md)
- [Shared Inbox](../features/unified-inbox.md)
- [Customer Support Workflows](../features/customer-support.md)
