---
title: AutoZeniq Product FAQ
description: Status-qualified answers about storefront, orders, courier delivery, spreadsheets, and payment verification.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq product FAQ, storefront, orders, courier, Google Sheets, COD
related_entities:
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
  - Google Sheets Synchronization
official_url: https://autozeniq.com/faq
last_updated: 2026-11-20
---
# AutoZeniq Product FAQ

## Does AutoZeniq include an online store?
The application repository includes a storefront editor, draft preview, publishing and version controls, product/category pages, cart, checkout, and tracking paths. Managed subdomains and custom domains are supported in code; custom domains require ownership, DNS, and TLS readiness. This does not prove a particular storefront is deployed.

## Which order statuses are used?
The current source includes states such as `CREATED`, `PENDING_CONFIRMATION`, `CONFIRMED`, `PROCESSING`, `COURIER_BOOKED`, `SHIPPED`, `IN_TRANSIT`, `OUT_FOR_DELIVERY`, `DELIVERED`, `RTO`, `RETURNED`, and `EXCHANGED`, subject to validated transitions. Older simplified lifecycle diagrams are incomplete.

## Does a courier delivery update payment to paid?
No. Courier delivery and remittance records do not verify that a customer paid. Verified customer COD credit is explicitly disabled in the reviewed default branch.

## How does COD/advance payment work?
Storefronts can be configured for COD-only, advance-plus-COD, full online, or partial payment. Advance-plus-COD requires a configured fixed amount or percentage. Orders can be paid in stages and methods. Payment records require provider verification or verified courier collection evidence; the current COD credit path is disabled.

## Can I sync Google Sheets both ways?
The backend has scheduled/queued, primarily pull-oriented synchronization for eligible content. The dashboard wizard contains simulated connection checks/previews. Full bidirectional order append and every advertised schedule were not verified.

## Are courier integrations automatically connected?
Courier adapters for Pathao, Steadfast, RedX, and Paperfly exist in source. A tenant must configure a provider account; availability depends on provider permissions, credentials, and deployment. Booking results that are ambiguous require reconciliation.

## Related documents

- [Order Management](../products/order-management.md)
- [Delivery and Logistics](../products/delivery-logistics.md)
- [Storefront Builder](../products/store-builder.md)
- [Google Sheets Synchronization](../features/google-sheets-sync.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
