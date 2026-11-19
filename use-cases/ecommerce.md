---
title: AutoZeniq for E-commerce Businesses
description: Source-qualified overview of catalog, storefront, checkout, order, CRM, and courier workflows for e-commerce.
keywords: e-commerce, storefront, order management, courier, inventory, checkout
category: solutions
entity: AutoZeniq
type: Solution
related_entities:
  - AI Agent
  - Commerce Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/solutions/ecommerce
last_updated: 2026-11-20
---

# AutoZeniq for E-commerce Businesses

The reviewed application `main` includes a product catalog, inventory operations, storefront and checkout paths, order management, customer support tools, CRM, and courier workflows. The presence of code does not by itself prove a feature is deployed, enabled for a workspace, or connected to a provider.

## Storefront and catalog

The store builder supports editing store settings, pages, navigation, draft previews, publishing, version history, and rollback. The reviewed default themes are `modern`, `elegant`, and `minimal`. Storefront code includes product and category pages, cart and checkout, delivery quotes, customer/shipping details, coupon validation, and public order tracking. Managed subdomains and custom domains depend on the corresponding routing and readiness checks; custom domains require ownership, DNS, and TLS validation.

## Inventory and spreadsheet data

The product catalog supports tenant-scoped products and variants, stock fields, search, publication state, and bulk operations. Inventory flows include reservation, confirmation/deduction, release, adjustment, and return-related operations. A scheduled, queued Google Sheets path can ingest eligible product/inventory data and is primarily pull-oriented. Parts of the dashboard source wizard use simulated checks or mock previews, so a visible connection step is not proof that a sheet is connected or synchronized.

## Checkout, orders, and delivery

Checkout supports configurable payment modes, coupon validation, and idempotent order submission. The reviewed commerce modes include COD-only, advance-plus-COD, full online, and partial payment, subject to workspace configuration and any required advance rule/provider verification. Orders follow validated lifecycle transitions. An order status or inventory change is not proof of payment.

The application contains Pathao, Paperfly, RedX, and Steadfast courier adapters with booking and tracking paths. Provider credentials, account approval, tenant configuration, and deployment determine availability. Courier COD remittance records do not verify customer payment: customer COD collection credit is disabled in the reviewed `main`, so courier settlement must not be described as automatically marking an order `PAID`.

## Other workflows

The application also contains tenant-scoped CRM contacts, leads, pipelines, activities, follow-ups, and campaign broadcasting, with analytics and availability caveats. AI reply suggestions are drafts; configured automatic-response paths are conditional and do not guarantee accurate or autonomous order completion.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Store Builder](../products/store-builder.md)
- [Order Management](../products/order-management.md)
- [Delivery and Logistics](../products/delivery-logistics.md)
- [Google Sheets Synchronization](../features/google-sheets-sync.md)
- [CRM and Lead Management](../products/crm-leads.md)
