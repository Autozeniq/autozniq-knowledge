---
title: Telegram Bot Connection
description: Telegram bot setup prerequisites, shared-inbox behavior, limitations, and error handling.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq Telegram, Telegram Bot, connection, shared inbox
related_entities:
  - Customer Support Workflows
  - Shared Inbox
official_url: https://autozeniq.com/integrations/telegram
last_updated: 2026-11-20
---
# Telegram Bot Connection

**Status: Configuration Required**

Telegram use requires a bot connection, workspace access, and the channel features enabled for the account. Confirm the current bot setup, credential handling, supported message types, and plan requirements in the official AutoZeniq documentation.

## Observable behavior

When the bot is connected and active, supported conversations may appear in the shared inbox. Agents can use the inbox features enabled for the workspace, such as history, human replies, assignment, and configured AI assistance. AI suggestions are drafts unless an automatic reply option is explicitly enabled.

## Limits and errors

Support for every Telegram media format, keyboard or interactive control, webhook behavior, message limit, and automatic reply is **Needs Verification**. If messages do not appear or replies fail, check the bot connection state, workspace settings, provider notices, and the current Telegram requirements. Do not assume a failed or delayed provider response means the message was delivered.

## Related documents

- [Shared Inbox](../features/unified-inbox.md)
- [Customer Support Workflows](../features/customer-support.md)
