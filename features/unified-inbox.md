---
title: Shared Inbox
description: Reviewed conversation search, message history, replies, assignment, AI controls, and provider-dependent channel paths.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq inbox, shared inbox, conversation management, agent assignment, messaging channels
related_entities:
  - Customer Support Automation
  - Conversation Management
  - AI Agent
official_url: https://autozeniq.com/features/omnichannel-inbox
last_updated: 2026-11-20
---

# Shared Inbox

The reviewed application `main` contains a tenant-scoped workspace for listing and searching conversations, viewing message history, sending human replies, assigning work, and pausing, taking over, or resuming AI handling. Selected real-time updates are available. Channel availability depends on provider connection, account permissions, workspace configuration, and deployment.

## Channels and media

Provider connection and webhook paths exist for supported services including WhatsApp, Facebook Messenger, Instagram, Telegram, TikTok, and the website widget. These integration paths do not prove that every provider is approved or that each message type is available in production. Text, image, and voice media upload/processing paths are present; do not infer exact file limits, universal playback/transcription, or availability across every channel.

## Assignment and AI controls

Agents can assign conversations and use configured AI assistance. AI Copilot reply suggestions are drafts for human review; separate guarded auto-reply paths depend on tenant settings and channel configuration. Do not promise automatic assignment based on agent load, collision locks, typing or presence indicators, read receipts, or internal notes.

## Limits

The reviewed source does not establish Shopify or WooCommerce customer purchase records in the inbox, a complete ticketing system, arbitrary workflow actions from the inbox, or sending every provider template message. Use the provider-specific integration documentation to verify any particular channel action.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Customer Support Workflows](./customer-support.md)
- [Conversation Management](./conversation-management.md)
- [Public API](../integrations/api.md)
