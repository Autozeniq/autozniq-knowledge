---
title: RedX Courier Integration Status
description: Merchant-facing RedX setup, pickup and address flow, COD boundary, and verification status.
entity: AutoZeniq
type: Integration
category: integrations
keywords: RedX courier integration, merchant account, pickup, address, COD, tracking
related_entities:
  - Delivery Logistics
  - Order Management System
official_url: https://autozeniq.com/docs/courier-redx
last_updated: 2026-11-20
---
# RedX Courier Integration

**Overall status: Needs Verification**

Public setup guidance for RedX confirms merchant account authorization and a pickup/address flow. Confirm the current AutoZeniq connection steps, account approval, exact fields, and supported operations with official documentation or support. Do not invent credential names or assume that account authorization activates every courier feature.

## Status matrix

| Area | Status | Merchant guidance |
|---|---|---|
| Credentials/setup | Configuration Required | Authorize the merchant account and complete the current pickup/address setup. Exact fields are Needs Verification. |
| Booking/AWB | Needs Verification | Confirm whether booking and AWB/consignment creation are enabled for the account. |
| Charges/COD | Needs Verification | Confirm current charges and COD collection options with RedX and AutoZeniq. |
| Tracking/status sync | Needs Verification | Confirm supported status visibility and refresh behavior. |
| Cancellation/returns/RTO | Needs Verification | Confirm cancellation, returns, reverse pickup, and RTO handling before relying on them. |
| COD settlement vs customer payment confirmation | Partially Available | COD collection is an instruction, not verified payment. Delivery or remittance must not by itself mark an order paid. |
| Failure/error handling | Needs Verification | Follow current provider errors and support guidance; reconcile ambiguous results before retrying. |

## Setup and limits

Test the connected merchant account with a controlled order and verify pickup, address, booking, and status results. Coverage, rate calculation, service levels, notifications, and return behavior remain **Needs Verification** unless confirmed for the account.

## Related documents

- [Delivery and Logistics](../products/delivery-logistics.md)
- [Order Management](../products/order-management.md)
