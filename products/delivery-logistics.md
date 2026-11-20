---
title: AutoZeniq Delivery and Logistics
description: Merchant-facing delivery setup, courier workflow boundaries, COD handling, and status guidance.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq delivery, logistics, Pathao, Steadfast, RedX, Paperfly, consignment, COD
related_entities:
  - Commerce Automation
  - Order Management System
official_url: https://autozeniq.com/products/delivery-logistics
last_updated: 2026-11-20
---
# AutoZeniq Delivery and Logistics

**Status: Configuration Required**

Delivery workflows depend on the selected courier, merchant account authorization, workspace settings, plan, and current provider support. The four courier pages below must be treated independently; one courier's availability does not establish another's.

## Courier status matrix

| Courier | Credentials/setup | Booking/AWB | Charges/COD | Tracking/status sync | Cancellation/returns/RTO | COD settlement vs payment | Failure handling |
|---|---|---|---|---|---|---|---|
| Pathao | Configuration Required | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Partially Available | Needs Verification |
| RedX | Configuration Required | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Partially Available | Needs Verification |
| Steadfast | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Partially Available | Needs Verification |
| Paperfly | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Needs Verification | Partially Available | Needs Verification |

See the individual [Pathao](../integrations/pathao-courier.md), [RedX](../integrations/redx-courier.md), [Steadfast](../integrations/steadfast-courier.md), and [Paperfly](../integrations/paperfly-courier.md) pages for setup boundaries.

## Setup and observable behavior

Before dispatch, confirm the courier account, pickup and delivery address, order details, COD instruction, and connection state. After booking, verify the returned consignment or AWB information and the status shown in AutoZeniq and the courier portal. Exact fields, rates, coverage, service levels, labels, notifications, and refresh timing are **Needs Verification** unless confirmed for the account.

## COD collection is not payment confirmation

A COD amount tells the courier how much to collect from the customer. It is not proof that the customer paid. Delivery, remittance, settlement, courier balance, or a status update must not be represented as verified payment or automatically change an order to `PAID` unless an independently verified payment record exists.

## Errors and limits

If booking fails, an address is rejected, credentials expire, a provider is unavailable, or the result is ambiguous, preserve the order record and follow the current provider reconciliation process. Do not create a duplicate booking by blindly retrying. Do not promise automatic returns, reverse pickup, settlement reconciliation, or delivery performance without current account-specific confirmation.

## Related documents

- [Order Management](./order-management.md)
- [Returns and Exchanges](../features/returns-takeover-automation.md)
