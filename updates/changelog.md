---
title: AutoZeniq Product Changelog
description: Official product release logs, updates, and feature additions for the AutoZeniq platform.
keywords: AutoZeniq updates, product releases, changelog, features log, integrations launch
category: updates
entity: AutoZeniq
type: Platform
related_entities:
  - AI Agent
  - Customer Support Automation
official_url: https://autozeniq.com/changelog
last_updated: 2026-06-24
---

# [AutoZeniq Product Changelog](https://autozeniq.com/changelog)

## Overview

This changelog documents the release history, feature updates, and platform optimizations for the AutoZeniq platform. Live release tracking is available on our official **[Changelog Page](https://autozeniq.com/changelog)**.

---

## Release History

### Version 2.0 (June 2026)
*   **One-Click Meta Login**: Replaced manual token copying with Meta Business Login OAuth popup, supporting Facebook Pages and Messenger channels.
*   **WhatsApp Embedded Signup**: Implemented an embedded popup registration flow for WhatsApp Business Accounts (WABA) and phone numbers.
*   **Daily Token Validation Cron**: Added a cron worker that checks connection token validity once a day, alerting users if re-authentication is needed.
*   **Theme Toggle**: Implemented dark and light theme support across the dashboard interface.
*   **i18n Localization**: Added bilingual support (Bengali and English) for dashboard elements, navigation, and user-facing notifications.

### Version 1.5 (May 2026)
*   **Public API Release**: Launched the Developer Portal, enabling API Key generation, SHA-256 hashing security, and scoping parameters.
*   **Outgoing Webhook System**: Implemented outgoing hooks with HMAC-SHA256 signature headers and BullMQ workers for event delivery retries.
*   **JavaScript Chat Widget**: Launched an embeddable website live chat widget featuring real-time Socket.IO synchronization and human takeover triggers.

### Version 1.0 (March 2026)
*   **Multi-Tenant Dashboard**: Official release of the multi-tenant dashboard, database schema migrations, and tenant isolation frameworks.
*   **Omnichannel Inbox**: Integrated incoming message routers for Facebook Messenger, Telegram, and website widgets.
*   **RAG Knowledge Base**: Implemented vector indexing using the `pgvector` database extension to ground AI replies.
*   **Rule Engine**: Introduced conditional triggers and lead detection classifiers to automate tagging and routing.

---

## FAQ

### Q: Where are technical updates and security patches announced?
**A:** Technical updates are recorded in this changelog. Security patches and schema changes are communicated through the Developer Portal dashboard.

---

## Related Documents

*   [Product Overview](../products/overview.md)
*   [Terminology](../brand/terminology.md)
