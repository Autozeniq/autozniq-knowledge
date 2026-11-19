---
title: AutoZeniq Product Relationships
description: Status-qualified map of product areas and their relationships in the reviewed AutoZeniq application.
entity: AutoZeniq
type: Company
category: company
keywords: AutoZeniq relationships, product map, commerce, platform modules
related_entities:
  - AI Agent
  - Commerce Automation
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/
last_updated: 2026-11-20
---

# AutoZeniq Product Relationships

The map below groups product areas found in the reviewed application `main`. It is a source-level relationship map, not a deployment diagram or a guarantee that every path is enabled for every workspace.

## Product area map

```text
AutoZeniq
├── Workspace and platform administration
│   ├── Membership, permissions, settings, entitlements
│   └── Selected Super Admin controls and audit views
├── Customer conversations
│   ├── Shared inbox, message history, replies, assignment
│   ├── AI Copilot drafts and configured AI response paths
│   ├── Knowledge ingestion and conversational retrieval
│   └── Human pause, takeover, and resume controls
├── Commerce
│   ├── Tenant-scoped products, variants, and inventory
│   ├── Store builder, storefront pages, cart, and checkout
│   ├── Orders, payment records, returns, and exchanges
│   └── Courier booking, tracking, and COD remittance records
├── Customer relationship management
│   ├── Contacts, leads, and deal pipelines
│   ├── Assignment, activities, work queue, and follow-ups
│   └── Entitlement-guarded campaign broadcasting
└── Integrations and operations
    ├── Scoped Public API, developer keys, and outgoing webhooks
    ├── Scheduled, queued, primarily pull-oriented Sheets ingestion
    ├── Limited workflow triggers and executable actions
    └── Security, notifications, billing, and analytics surfaces
```

## Important relationship boundaries

- **Orders and payment:** an order lifecycle status, stock change, courier remittance, or settlement record is not proof of verified customer payment. Customer COD collection credit is disabled in the reviewed `main`.
- **Sheets and catalog:** the verified Sheets flow is primarily pull-oriented. Full bidirectional synchronization and every dashboard connection step were not established.
- **Workflows:** connected triggers and executable actions are limited; unsupported actions fail closed. See [Automation](./features/automation.md).
- **AI and support:** Copilot suggestions are drafts. Automatic responses depend on guarded paths and configuration; retrieval does not guarantee correctness.
- **Integrations:** source adapters and connection code do not prove provider approval, live credentials, or production availability.

For the full status and evidence boundaries, see the [Current Feature Inventory](./docs/current-feature-inventory.md).

## Related documents

- [Entity Profile](./entity-profile.md)
- [Capabilities Catalog](./capabilities.md)
- [Store Builder](./products/store-builder.md)
- [Order Management](./products/order-management.md)
- [Delivery and Logistics](./products/delivery-logistics.md)
- [System Architecture](./docs/system-architecture.md)
