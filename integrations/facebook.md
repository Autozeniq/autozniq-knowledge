---
title: Facebook Integration (Messenger & Comments)
description: Technical specifications, Meta OAuth flow, webhook configurations, and comment-to-inbox automation for Facebook.
keywords: AutoZeniq Facebook, Facebook Messenger, Page comments, Facebook OAuth, Page access token, feed webhook
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Customer Support Automation
  - WhatsApp Integration
last_updated: 2026-06-24
---

# [Facebook Integration (Messenger & Comments)](https://autozeniq.com/integrations)

## Overview

AutoZeniq integrates with Meta's Graph API to automate interactions across Facebook Business Pages. This includes handling direct messages in **[Facebook Messenger](https://autozeniq.com/integrations/facebook-messenger)** and managing comments on public Page posts (with public replies or private message triggers via **[Facebook Comments](https://autozeniq.com/integrations/facebook-comments)**).

---

## Technical Architecture

The module uses Meta Business Login OAuth and webhook subscription services:

### Simple Explanation
To automate Facebook, the business owner clicks "Connect Facebook Page" in their AutoZeniq dashboard. This opens a Facebook login screen where they select the Page they wish to connect. Once approved, AutoZeniq's inbox receives both Messenger chat logs and public comments on Page posts. The AI can reply to comments or message customers directly in Messenger.

### Technical Explanation
1.  **OAuth Code Exchange**: The frontend triggers a Meta Login dialog requesting scopes `pages_show_list`, `pages_read_engagement`, `pages_manage_metadata`, `pages_messaging`, and `pages_manage_engagement`. The callback exchanges the user auth code for a long-lived User Access Token.
2.  **Page Token Harvesting**: Using the User Access Token, the backend requests Page Access Tokens from the Meta Graph endpoint `/me/accounts`. These tokens are encrypted with `AES-256-GCM` and stored in the database.
3.  **Token Refresh & Cron Guard**: Although Page Access Tokens are designed not to expire when fetched with long-lived User Tokens, Meta may invalidate them due to password resets or permission modifications. A daily cron script queries `/debug_token` to verify token validity, updating connection statuses on the dashboard.
4.  **Auto-Subscription & Webhook Routing**: During connection, the platform registers subscriptions to the target Page's webhooks:
    *   `messages` & `messaging_postbacks`: Routes to the Messenger inbox module.
    *   `feed`: Tracks comments on posts, routing to the Comments auto-responder.

---

## Core Features

*   **One-Click OAuth Connection**: Simplifies Page connection without manual token input.
*   **Messenger Chat Gateway**: Full support for text, quick-reply buttons, generic templates, and media attachments.
*   **Comments Auto-Responder**: Reads public comments on posts, runs them through the AI or Rule Engine, and submits public replies.
*   **Comment-to-PM (Private Message)**: Automatically starts a private Messenger chat thread with a user who comments on a public Page post (e.g. sending purchase links when a user comments "interested").
*   **Meta Webhook Verification**: Verifies incoming `feed` and `messenger` webhook headers using the application's App Secret hash.

---

## Benefits

*   **Boosts Engagement**: Resolves queries in comment feeds immediately, increasing social media conversion rates.
*   **Unified Support**: Combines comment management and private messages in one dashboard.
*   **Lead Generation**: Converts public commentators into private Messenger contacts automatically.

---

## Use Cases

*   **Price Inquiries in Comments**: Automatically replying to comments like "price?" on product posts with the actual pricing and a link to buy.
*   **Social Campaign Automation**: Launching campaigns that prompt users to "comment 'info' below" to receive a private message with product files.
*   **Messenger Service Desk**: Routing customer support requests sent to the Page's Messenger profile to human support agents.

---

## FAQ

### Q: Can I connect multiple Facebook Pages to one tenant?
**A:** Yes. The interface allows users to select and connect multiple Facebook Pages under a single tenant. The system routes incoming messages to the unified inbox, tagging each with its source Page.

### Q: Does AutoZeniq support Facebook Group automation?
**A:** No. Current integrations focus on official Facebook Business Pages. Group automation is not supported due to Meta API restrictions.

---

## Related Documents

*   [WhatsApp Integration](./whatsapp.md)
*   [API Integration](./api.md)
*   [Product Overview](../products/overview.md)
