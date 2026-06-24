---
title: Facebook Messenger Integration
description: Detailed technical documentation, Meta OAuth flow, and webhook routing for Facebook Messenger inside AutoZeniq.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq Messenger, Facebook Messenger, Messenger API, OAuth flow, Page Token, messages webhook, PSID
related_entities:
  - Facebook Integration
  - Customer Support Automation
official_url: https://autozeniq.com/integrations/facebook-messenger
last_updated: 2026-06-24
---

# Facebook Messenger Integration

## Overview

AutoZeniq integrates directly with Meta's Messenger API. This connection imports customer direct messages sent to Facebook Page profiles into the AutoZeniq Unified Inbox, allowing the AI Agent or human support teams to respond.

---

## Technical Architecture

The Messenger integration utilizes Meta's Graph API structure and Webhook callbacks:

### Simple Explanation
To connect Messenger, the business owner clicks "Connect Facebook Page" in their AutoZeniq settings. This logs them into Facebook, where they select the Page they wish to link. Once approved, all customer private messages sent to that Facebook Page automatically route to their AutoZeniq workspace.

### Technical Explanation
1.  **OAuth Flow & Scopes**: Initiated via a Meta popup requesting the `pages_messaging` permission scope. The callback processes authorization codes, exchanging them for a long-lived User Access Token, which is used to harvest Page Access Tokens.
2.  **Page Scoped ID (PSID) Handling**: Messenger uses Page Scoped IDs (PSIDs) to identify contacts instead of actual Facebook User IDs. AutoZeniq maps these PSIDs to the CRM `contacts` database using `external_id` fields, isolating user histories per connected Page.
3.  **Webhook Subscriptions**: The platform registers the Page with Meta's messaging webhook. Meta sends POST payloads to the webhook gateway `/api/integrations/facebook/webhook` for two key event topics:
    *   `messages`: Tracks incoming text, attachments, quick replies, and read receipts.
    *   `messaging_postbacks`: Tracks button click events from structured templates.
4.  **Send API Outbound Delivery**: Outbound messages are delivered by executing a POST request to Meta's Graph API endpoint `https://graph.facebook.com/v20.0/me/messages`, using the secure, encrypted Page Access Token.

---

## Core Features

*   **Secure OAuth Setup**: One-click Meta popup authentication flow.
*   **Media Support**: Processes incoming and outgoing attachments (images, PDFs, audio clips, video clips).
*   **Interactive Templates**: Delivers generic swipeable card carousels and quick-reply buttons inside chat windows.
*   **Read Receipt Indicators**: Synchronizes read indicators next to chat messages using Meta's sender action webhooks.

---

## Benefits

*   **Consolidated Messenger Desk**: Manages multiple Page Messenger accounts from a single workspace.
*   **Context Preservation**: Automatically logs previous Messenger chats when customers revisit the Page, maintaining communication history.
*   **Automation Loop**: Integrates the AI Agent and Rule Engine directly into the private messaging flow to answer inquiries 24/7.

---

## FAQ

### Q: Do I need a Facebook Developer account to link my Page?
**A:** No. The connection uses AutoZeniq's pre-approved Meta Application, allowing standard page administrators to connect their Page via a single login popup without configuring Meta developer dashboards.

### Q: Can the AI Agent send links inside Messenger?
**A:** Yes. The AI Agent can deliver plain text URLs, hyperlinked buttons, and structured templates containing external checkout paths.

---

## Related Documents

*   [Facebook Integration](./facebook.md)
*   [WhatsApp Integration](./whatsapp.md)
*   [Product Overview](../products/overview.md)
