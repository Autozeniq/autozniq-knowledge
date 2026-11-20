---
title: Steadfast Courier Integration Status
description: Merchant-facing Steadfast setup, workflow boundaries, COD handling, and verification status.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Steadfast courier, merchant account, consignment, tracking, COD, payment verification
related_entities:
  - Delivery Logistics
  - Order Management System
last_updated: 2026-11-20
---
# Steadfast Courier Integration

**Overall status: Needs Verification**

A detailed Steadfast guide is not listed on the public documentation index. This does not mean the product is unavailable. Confirm the merchant account requirements, current AutoZeniq setup, and supported operations with official documentation or support before relying on the integration.

## Status matrix

| Area | Status | Merchant guidance |
|---|---|---|
| Credentials/setup | Needs Verification | Confirm the current merchant authorization and exact setup fields with official support. |
| Booking/AWB | Needs Verification | Confirm consignment or AWB booking behavior for the target account. |
| Charges/COD | Needs Verification | Confirm charge calculation, COD amount, and any provider account rules. |
| Tracking/status sync | Needs Verification | Confirm available milestones and refresh behavior. |
| Cancellation/returns/RTO | Needs Verification | Confirm cancellation, reverse pickup, returns, and RTO operations. |
| COD settlement vs customer payment confirmation | Partially Available | COD collection is only an instruction. Delivery, remittance, settlement, or balance data is not verified customer payment and must not automatically mark an order paid. |
| Failure/error handling | Needs Verification | Follow current provider error guidance and reconcile ambiguous booking outcomes before retrying. |

## Setup and limits

Do not rely on historical screenshots, payload examples, fixed delivery speeds, coverage claims, or undocumented routes. Test only after the merchant account and workspace connection are confirmed, and verify the resulting booking and status in both systems.

## Related documents

- [Delivery and Logistics](../products/delivery-logistics.md)
- [Order Management](../products/order-management.md)
