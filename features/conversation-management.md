---
title: Conversation Management and Shared Inbox
description: Current conversation search, message history, human reply, assignment, AI controls, and media paths.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq inbox, conversation management, CRM context, media, assignment, AI handover
related_entities:
  - Customer Support Automation
  - Order Management System
  - CRM and Lead Management
  - Media Processing
official_url: https://autozeniq.com/features/omnichannel-inbox
last_updated: 2026-11-20
---

# Conversation Management and Shared Inbox

The reviewed application `main` includes a tenant-scoped inbox for conversation search and listing, message history, human replies, assignment, AI pause/takeover/resume, and selected real-time updates. Text, image, and voice media upload/processing paths are present. Provider, channel, workspace, and deployment configuration determine what a particular agent can use.

## AI and human handling

AI Copilot can prepare reply suggestions for agent review. Guarded AI auto-reply paths are also present, but they depend on configuration and provider setup. A suggestion is not a sent message, and retrieval does not guarantee that an answer is correct. Agents can pause or take over AI handling where the conversation supports it.

## Related customer and order workflows

The inbox and CRM/order modules exist in the same application, but the reviewed source does not establish every CRM field or order action as a live sidebar feature. Do not promise that the inbox universally shows phone-verification badges, lifetime value, return percentages, fraud scores, Quick Order creation, or customer order history unless the specific interface and deployment are separately verified.

## Real-time and collaboration limits

Some WebSocket updates are implemented, but universal presence, typing indicators, read receipts, collision locks, internal notes, and guaranteed duplicate-reply prevention were not established by the reviewed source. No measured chat-to-sale conversion uplift or tool-switching reduction is available.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Shared Inbox](./unified-inbox.md)
- [Customer Support Workflows](./customer-support.md)
- [Order Management](../products/order-management.md)
- [CRM and Lead Management](../products/crm-leads.md)
- [Media Processing](./multimodal-processing.md)
