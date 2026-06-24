---
title: Conversation Management Features
description: Features of the AutoZeniq conversation management workspace, detailing the unified inbox, contact profiles, and thread state lifecycle.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq inbox, unified inbox, CRM profiles, thread state, web sockets, message history
related_entities:
  - Customer Support Automation
  - Terminology
official_url: https://autozeniq.com/features/omnichannel-inbox
last_updated: 2026-06-24
---

# [Conversation Management Features](https://autozeniq.com/features/omnichannel-inbox)

## Overview

The [AutoZeniq Conversation Management workspace](https://autozeniq.com/features/omnichannel-inbox) provides agents with a unified system to monitor, filter, and reply to client messages. It binds [CRM contact profiles](https://autozeniq.com/features/crm) directly to active chat threads, ensuring that agent teams have access to client history, custom tags, and transaction logs.

---

## Technical Architecture

This module manages real-time messaging states and database lookups:

### Simple Explanation
When a customer sends a message on WhatsApp or Facebook, it appears in a single shared inbox on the AutoZeniq dashboard. Next to the chat, the support agent can see the customer's name, phone number, custom notes, and a list of their past purchases. This saves agents from having to switch between messaging apps and e-commerce platforms.

### Technical Explanation
1.  **State Lifecycle Engine**: Conversations are mapped in the database with status fields (`unassigned`, `ai`, `open`, `closed`). Transitioning the status silences or resumes AI responders.
2.  **WebSocket Gateways**: Uses `Socket.IO` to broadcast webhook message events to front-end dashboard subscribers. This updates the message feeds and unread badges in real time.
3.  **CRM Profile Association**: Incoming webhook payloads search the `contacts` table for matching identifiers (e.g., WhatsApp phone number or Facebook scoped ID). If found, the contact card is rendered in the dashboard; if not, a new contact is created.

---

## Core Features

*   **[Unified Inbox](https://autozeniq.com/features/omnichannel-inbox)**: A dashboard pane showing active messaging threads from WhatsApp Business, Facebook Messenger, Facebook Comments, Instagram DM, Telegram, and website chat widgets.
*   **[CRM Contact Card](https://autozeniq.com/features/crm)**: A panel beside the chat window displaying the customer's phone number, email address, custom field metadata (e.g., shipping address), and order logs.
*   **Conversation Lifecycle States**:
    *   `ai`: Auto-responding using knowledge base documents.
    *   `open`: Human agent managing replies (AI silenced).
    *   `closed`: Interaction resolved.
*   **Thread Search & Filters**: Search tools to query conversation lists by channel type, tags, assigned agent, status, or keyword content.
*   **Collaborative Handover Notes**: Private internal threads allowing support agents to log notes and coordinate with other team members without exposing these notes to the client.

---

## Benefits

*   **Channel Unification**: Unifies chat streams into a single dashboard.
*   **Context Preservation**: Retains complete history when re-routing threads or transitioning from AI to human operators.
*   **Team Collaboration**: Minimizes overlapping replies by showing which agent is currently viewing or typing in a thread.

---

## Use Cases

*   **Multi-Channel Continuity**: Resolving a customer's query on WhatsApp while reviewing their past chat logs from Facebook Messenger.
*   **Customer Segmentation**: Tagging a contact as a "Wholesaler" during a chat so the Rule Engine can apply custom pricing rules in future interactions.
*   **Support Team Handover**: Assigning a complex billing issue to the finance team's inbox queue with an explanatory internal note.

---

## FAQ

### Q: Does AutoZeniq track read receipts?
**A:** Yes. The unified inbox processes delivery and read webhooks sent by channels (such as WhatsApp) and displays standard read receipts next to message text bubbles.

### Q: Can agents send images or files through the unified inbox?
**A:** Yes. Agents can upload and send attachments (images, PDFs, voice recordings) which are securely stored on Cloudflare R2 and delivered via the appropriate channel API.

---

## Related Documents

*   [Customer Support Features](./customer-support.md)
*   [Automation Features](./automation.md)
*   [Integrations Overview](../products/overview.md)
