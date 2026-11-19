---
title: AutoZeniq E-commerce Capabilities
description: Status-qualified overview of storefront, order, messaging, courier, catalog, and CRM capabilities for online sellers.
entity: AutoZeniq
type: Solution
category: solutions
keywords: AutoZeniq ecommerce, online sellers, storefront, orders, couriers, Google Sheets
related_entities:
  - AI Agent
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/solutions/ecommerce
last_updated: 2026-11-20
---
# AutoZeniq E-commerce Capabilities

AutoZeniq's application `main` includes tenant-workspace tools for online sellers: a shared customer inbox, AI assistance, a store builder and checkout, order and inventory management, courier integrations, knowledge sources, CRM, and selected reporting. Which functions are available depends on the workspace plan, settings, provider access, and deployment.

## What the codebase supports

- **Storefront:** edit and publish tenant pages, preview drafts, manage versions, and configure managed/custom domains. Custom domains require verified ownership, DNS, and TLS readiness.
- **Orders and catalog:** manage products and variants, inventory, checkout, order lifecycle, payment records, and merchant-mediated returns/exchanges.
- **Delivery:** adapters for Pathao, Steadfast, RedX, and Paperfly are present with booking/tracking flows; live use requires account credentials and provider readiness.
- **Google Sheets:** queued, scheduled, primarily pull-oriented synchronization can classify tabs and map common English/Bengali catalog headers. The dashboard wizard has simulated states in parts; bidirectional order append is not verified.
- **CRM and messaging:** tenant-scoped contacts, leads, deals, follow-ups, campaigns, supported messaging-provider paths, and AI suggestions.

## Payment and courier note

Store checkout can be configured for COD-only, advance-plus-COD, full online, or partial payment. An advance-plus-COD rule must specify an amount or percentage. Online capture requires server-side provider verification. Verified customer COD collection credit is currently disabled; courier delivery/remittance records are not proof that the customer paid and do not automatically mark an order paid.

## Availability caveat

An adapter, screen, API path, or test in the source repository is not evidence of production deployment, connected provider accounts, published availability, or measured outcomes. Refer to the [Current Feature Inventory](../docs/current-feature-inventory.md) for status details.

## Related documents

- [Products Overview](../products/overview.md)
- [Order Management](../products/order-management.md)
- [Delivery and Logistics](../products/delivery-logistics.md)
- [Storefront Builder](../products/store-builder.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
