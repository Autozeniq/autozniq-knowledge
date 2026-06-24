---
title: Unified Inbox Feature
description: Detailed technical details, channel aggregation, and WebSocket architecture of the AutoZeniq Unified Inbox.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq inbox, Unified Inbox, omnichannel inbox, chat routing, agent seats, message aggregation
related_entities:
  - Customer Support Automation
  - Terminology
official_url: https://autozeniq.com/features/omnichannel-inbox
last_updated: 2026-06-24
---

# Unified Inbox Feature

## Overview

The AutoZeniq **Unified Inbox** (also referenced as the **Omnichannel Inbox**) is a collaborative message-routing workspace. It aggregates incoming communications from Facebook Messenger, Facebook Comments, WhatsApp Business API, Instagram Direct, Telegram, and website live chat widgets into a single dashboard.

---

## Technical Architecture

The inbox functions as a real-time event distribution hub:

### Simple Explanation
Instead of support staff logging into Facebook, opening WhatsApp on a phone, and checking website chats separately, all messages appear in a single inbox. Agents can read messages, reply, assign tasks, and see customer profiles on one screen.

### Technical Explanation
1.  **Normalization Layer**: Webhooks from different platform APIs are parsed by respective channel modules (e.g. `src/modules/integrations/whatsapp/`). The payload metadata (sender IDs, message formats) is normalized into a standard structure.
2.  **Thread Allocation**: Incoming messages trigger lookup queries in the `conversations` table. If an active thread exists, the message is appended; otherwise, a new thread is created under the state `unassigned` (or routed to the `ai` responder).
3.  **Real-Time Broadcast (Socket.IO)**: The NestJS backend utilizes WebSockets to push new messages to connected agent dashboard browsers in real time, segmented by tenant workspace.
4.  **Agent Collision Guard**: To prevent multiple agents from replying to the same customer simultaneously, the system uses WebSocket room connections to broadcast typing indicators and lock threads when an agent opens them.

---

## Core Features

*   **Omnichannel Consolidation**: Aggregates Facebook comments, DMs, WhatsApp chats, and web widget streams.
*   **Agent Assignment Queues**: Allows administrators to manually assign threads or configure automated routing rules based on agent load.
*   **CRM Sidebar Card**: Displays contact metrics, tags, custom attributes, and storefront purchase records from Shopify or WooCommerce.
*   **Internal Notes Overlay**: Private, team-only comments written directly within customer chat logs to facilitate team handover.
*   **Multi-Media Support**: Handles incoming and outgoing files, images, voice recordings, and documents, securely stored on Cloudflare R2.

---

## Benefits

*   **Eliminates App Switching**: Consolidates multiple communication tools into a single page.
*   **Reduces Duplicate Replies**: Shows typing states to prevent multiple support agents from responding to the same ticket.
*   **Retains Thread Context**: Displays past orders, customer tags, and internal notes alongside current chats.

---

## FAQ

### Q: Does the inbox support Telegram bots?
**A:** Yes. Once a Telegram Bot Token is connected, customer messages sent to your Telegram bot are routed to the unified inbox.

### Q: Can agents send WhatsApp Template Messages from the inbox?
**A:** Yes. Outside the standard 24-hour conversational window, the UI displays the merchant's pre-approved Meta message templates for outbound dispatches.

---

## Related Documents

*   [Customer Support Features](./customer-support.md)
*   [Conversation Management](./conversation-management.md)
*   [API Integration](../integrations/api.md)
