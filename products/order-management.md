---
title: AutoZeniq Order Management System
description: Merchant order workflow, inventory handling, delivery handoff, returns, and payment evidence boundaries.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq OMS, orders, order status, inventory, payment modes, checkout
related_entities:
  - Storefront Builder
  - Delivery Logistics
  - Returns and Exchanges
official_url: https://autozeniq.com/products/order-management
last_updated: 2026-11-20
---
# AutoZeniq Order Management System

**Status: Partially Available.** Merchant order records and selected checkout, review, inventory, payment-record, delivery-handoff, and support workflows are supported where enabled. Exact actions and statuses vary by workspace configuration and connected services.

## Order lifecycle

**Status: Partially Available.** An order can move through configured creation, confirmation, processing, courier, delivery, return, or exchange stages. The exact status names, allowed transitions, and automatic updates are **Needs Verification** for the workspace. A displayed status is a workflow state, not proof of payment.

## Inventory and delivery

Configured workflows can reserve, deduct, release, adjust, or restock inventory. Review the resulting stock and order record after cancellation, return, or exchange; do not assume every status change automatically restocks. Courier booking and tracking require the selected courier connection and account authorization. See [Delivery and Logistics](./delivery-logistics.md).

## Payment evidence

**Status: Partially Available.** Payment records should be based on verified online-provider evidence or another independently verified payment record. COD collection instructions tell a courier what to collect; they do not prove the customer paid. Courier delivery, remittance, settlement, or balance information must not automatically mark an order `PAID`.

## Returns and exchanges

**Status: Configuration Required.** Merchants may manage eligible return or exchange requests in the configured workflow. Approval, restocking, replacement stock, reverse pickup, and refunds are separate actions. A return record or courier event is not proof that a refund was issued.

## Errors and support

For duplicate submissions, rejected addresses, stock conflicts, provider failures, or ambiguous payment/delivery results, keep the order record, review the visible error, and use the documented reconciliation path. Do not create duplicate orders or bookings by blindly retrying.

## Related documents

- [Storefront Builder](./store-builder.md)
- [Delivery and Logistics](./delivery-logistics.md)
- [Returns and Exchanges](../features/returns-takeover-automation.md)
