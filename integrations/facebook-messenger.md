---
title: Facebook Messenger Connection
description: Merchant-facing Messenger setup prerequisites, observable inbox behavior, and provider limitations.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq Messenger, Facebook Messenger, Meta connection, shared inbox
related_entities:
  - Facebook Integration
  - Meta Account Connection
  - Shared Inbox
official_url: https://autozeniq.com/integrations/facebook-messenger
last_updated: 2026-11-20
---
# Facebook Messenger Connection

**Status: Configuration Required**

Messenger use requires an eligible Meta connection, a Page and workspace configuration, provider approval where required, and the features enabled for the account. A saved connection is not proof that every message type or automation is available.

## Setup prerequisites

Confirm the current Meta requirements, Page access, workspace permissions, and AutoZeniq plan in the official connection flow. Exact permission names, account limits, media support, and setup screens are **Needs Verification**.

## Observable behavior

When connected and enabled, conversations may appear in the shared inbox. Agents can use the features enabled for the workspace, such as viewing conversation history, replying, assignment, and configured AI assistance. AI suggestions are drafts unless the workspace explicitly enables an automatic reply path.

## Limitations and errors

Do not assume support for read receipts, public Page-comment replies, comment-to-private-message follow-up, every attachment, templates, or interactive messages. Provider approval, expired access, missing Page permissions, disabled channel settings, and workspace limits can prevent delivery or receiving messages. Check the connection state and provider notices; do not retry or promise delivery when the provider result is unclear.

## Related documents

- [Facebook Page comments](./facebook.md)
- [Meta Account Connection](./meta-oauth.md)
- [Shared Inbox](../features/unified-inbox.md)
