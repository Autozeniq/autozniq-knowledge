---
title: WhatsApp Business Connection
description: WhatsApp Business setup prerequisites, observable inbox behavior, provider approval, and limitations.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq WhatsApp, WhatsApp Business, Embedded Signup, connection
related_entities:
  - Customer Support Workflows
  - Meta Account Connection
  - Shared Inbox
official_url: https://autozeniq.com/integrations/whatsapp
last_updated: 2026-11-20
---
# WhatsApp Business Connection

**Status: Configuration Required**

WhatsApp use depends on a connected WhatsApp Business account and phone number, Meta requirements, workspace settings, provider approval, and plan entitlement. Confirm the current Embedded Signup or connection flow and required account state in the official documentation.

## Setup prerequisites

Use an authorized Meta business account, select the intended business assets, complete any required verification, and confirm the phone number and account shown after setup. Keep provider credentials private and do not assume that a successful consent screen means messaging is live.

## Observable behavior

When connected and enabled, supported conversations may appear in the shared inbox. Human replies, assignment, message history, and AI assistance depend on workspace configuration. AI suggestions are drafts; automatic sending requires an explicitly enabled and supported channel workflow.

## Limitations and errors

Support for every template, interactive message, location, media type, order notification, delivery window, or read status is **Needs Verification**. Provider review, phone-number status, missing permission, expired connection, message-policy restrictions, and workspace limits can block sending or receiving. Check the displayed connection and provider error, then use the official reconnect process; do not retry a state-changing action blindly.

See [Meta Account Connection](./meta-oauth.md) and [Shared Inbox](../features/unified-inbox.md).
