---
title: AutoZeniq Order Management System
description: Tenant order workflows, validated lifecycle states, inventory controls, storefront checkout, and payment evidence.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq OMS, orders, order status, inventory, payment modes, staged payment, checkout
related_entities:
  - Commerce Automation
  - Storefront Builder
  - Delivery Logistics
official_url: https://autozeniq.com/products/order-management
last_updated: 2026-11-20
---
# AutoZeniq Order Management System

The order system manages tenant-scoped orders from storefront checkout and supported merchant workflows. Order creation records items and payment details, applies configured coupons and delivery totals where eligible, writes timeline/outbox records transactionally, and evaluates available fraud-risk signals. Order identifiers use a generated `ORD-YYYYMMDD-XXXXXXXX` format.

## Order lifecycle

Current source uses validated transitions across states including `CREATED`, `PENDING_CONFIRMATION`, `CONFIRMED`, `PROCESSING`, `COURIER_BOOKED`, `SHIPPED`, `IN_TRANSIT`, `OUT_FOR_DELIVERY`, `DELIVERED`, `RTO`, `RETURNED`, and `EXCHANGED`. Exact transitions depend on the order state machine and provider events. Older diagrams listing only `PENDING → CONFIRMED → PROCESSING → SHIPPED → DELIVERED` are incomplete.

## Inventory

Inventory operations distinguish reservation, confirmation/deduction, release, adjustment, and restocking. Order and stock updates use transaction/locking controls in the reviewed paths. Cancellation, approved returns, and return-to-origin have separate handling; do not describe every status change as an automatic restock.

## Storefront and payment records

The storefront supports cart/checkout, delivery quotes, customer and shipping details, configured payment modes, coupon validation, idempotent order submission, and order tracking. Tenant payment settings can support COD-only, advance-plus-COD, full online, and partial payment. Advance-plus-COD requires a configured fixed amount or percentage. Orders may be paid in several stages and by different methods.

Payment records must be grounded in evidence: server-side provider verification for online captures, or verified courier collection evidence for COD credit. Current main explicitly disables verified customer COD collection credit. Courier remittance/settlement records do not prove that a customer paid and do not automatically make the order `PAID`.

## Reviews and returns

A customer review requires signed purchase verification and an eligible delivered order. Merchants can manage return/exchange requests for delivered orders, approve or reject them, and restock eligible approved quantities or check replacement stock. The reviewed implementation does not establish a shopper self-service return submission flow or an automatic refund transfer processor.

## Fraud controls and related integrations

Fraud scoring evaluates selected tenant-local and anonymized historical signals and can return risk factors and recommendations. Conditional courier auto-booking may apply a configured low-risk threshold. Do not make guarantees about fraud prevention or outcomes without measured evidence.

## FAQ

### Does a courier settlement update an order to paid?
No. A remittance record is not verified customer-collection evidence. The reviewed default-branch code explicitly disables verified COD collection credit.

### Is every returned order automatically restocked or refunded?
No. Return approval, eligible restocking, exchange handling, and refund transfers are distinct. The reviewed code does not prove automatic refund execution.

## Related documents

- [Storefront Builder](./store-builder.md)
- [Delivery & Logistics](./delivery-logistics.md)
- [Pricing and Subscription Billing](../pricing.md)
- [Billing and Entitlements](../features/billing-entitlements.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
