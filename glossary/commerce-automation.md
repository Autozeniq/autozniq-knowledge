---
title: Commerce Automation
description: Plain-language definition of commerce automation and the verified commerce workflows and limitations in AutoZeniq.
keywords: commerce automation, storefront, order management, courier, Google Sheets, inventory
category: glossary
entity: Commerce Automation
type: Glossary
related_entities:
  - AutoZeniq
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/solutions/ecommerce
last_updated: 2026-11-20
---

# Commerce Automation

## Definition

**Commerce automation** uses software to assist or coordinate product catalog, inventory, order, payment, storefront, and delivery workflows. Automation does not mean that every step is unattended, every payment is verified, or every connected provider is live.

## In AutoZeniq

The reviewed application `main` includes tenant-scoped product and variant records, inventory operations, storefront and checkout paths, configurable payment modes, order lifecycle handling, return/exchange operations, and courier booking/tracking paths. Availability depends on permissions, workspace settings, entitlements, provider credentials, and deployment.

The Google Sheets integration is a scheduled, queued, primarily pull-oriented ingestion path. Full bidirectional synchronization and general Shopify/WooCommerce integrations were not established by the reviewed source. Courier COD remittance records are distinct from verified customer payment; customer COD collection credit is disabled in the reviewed `main`.

See [E-commerce Solutions](../solutions/ecommerce.md), [Order Management](../products/order-management.md), [Delivery and Logistics](../products/delivery-logistics.md), and the [Current Feature Inventory](../docs/current-feature-inventory.md) for details.
