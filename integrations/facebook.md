---
title: Facebook Page Comments Integration Status
description: Current status and verification boundary for Facebook Page comment replies and follow-up messaging.
entity: AutoZeniq
type: Integration Status
category: integrations
keywords: Facebook comments, Page comments, public reply, private message, Meta
related_entities:
  - Facebook Messenger
  - Meta Account Connection
official_url: https://autozeniq.com/integrations/facebook-comments
last_updated: 2026-11-20
---
# Facebook Page Comments Integration Status

**Status: Needs Verification**

Do not promise that AutoZeniq can publish public replies to Page comments, trigger private messages from comments, respond to keywords, or create leads from comments. A Messenger connection alone does not establish any of those capabilities.

## Before relying on this workflow

Confirm the exact Page, Meta permissions, account approval, workspace settings, supported comment actions, and current provider documentation with AutoZeniq support. Test with a non-critical comment before using the workflow operationally.

## Observable behavior and errors

If the feature is enabled for the account, the connected channel should show its current connection state and any provider error. Missing permissions, provider review, unsupported message types, or an expired connection can prevent an action. Treat an absent or ambiguous result as unconfirmed; do not represent a comment as answered or a lead as captured until it is visibly confirmed.

See [Facebook Messenger](./facebook-messenger.md) and [Meta Account Connection](./meta-oauth.md) for related channel setup.
