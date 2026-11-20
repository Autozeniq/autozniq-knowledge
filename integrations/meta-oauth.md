---
title: Meta Account Connection Status
description: Meta connection prerequisites, approval dependencies, observable status, and recovery guidance.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Meta connection, Facebook, Instagram, WhatsApp, account connection
related_entities:
  - Facebook Messenger
  - WhatsApp Business Connection
  - Shared Inbox
official_url: https://autozeniq.com/integrations/meta-oauth
last_updated: 2026-11-20
---
# Meta Account Connection Status

**Status: Configuration Required**

Meta channel connections depend on the relevant business or Page access, provider approval, workspace permissions, account status, and AutoZeniq plan. The exact connection flow, permission list, supported channels, and account requirements are **Needs Verification**; use the current official connection flow or ask support.

## Setup prerequisites

Use an authorized Meta account, select only the intended business assets, and review the consent screen before completing the connection. Confirm that the selected Page, Instagram account, or WhatsApp Business account is the one the workspace should use. Do not share access tokens or paste them into support requests.

## Observable behavior

A successful connection should show the current account or channel state in the supported AutoZeniq settings and may allow the enabled channel to receive or send messages. Connection status is not a guarantee that every media type, template, comment action, or automation is supported.

## Errors and recovery

Common blockers include missing asset permission, provider review or business verification, an expired or revoked connection, an already-used account, or a workspace entitlement limit. Follow the current reconnect or disconnect flow, then verify the displayed account and channel state. If the provider result is ambiguous, stop and contact AutoZeniq or Meta support rather than creating duplicate connections.

See [Facebook Messenger](./facebook-messenger.md) and [WhatsApp](./whatsapp.md).
