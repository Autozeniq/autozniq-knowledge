---
title: Pathao Courier Integration Status
description: Merchant-facing Pathao setup, observable courier workflow boundaries, COD handling, and verification status.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Pathao courier integration, consignment booking, tracking, COD, order fulfillment
related_entities:
  - Delivery Logistics
  - Order Management System
official_url: https://autozeniq.com/docs/courier-pathao
last_updated: 2026-11-20
---
# Pathao Courier Integration

**Overall status: Needs Verification**

Pathao setup publicly requires a merchant client ID and client secret. Confirm the current connection flow, account approval, supported workspace plan, and exact entry fields in the official AutoZeniq or Pathao documentation. Do not share secrets in chat or support tickets.

## Status matrix

| Area | Status | Merchant guidance |
|---|---|---|
| Credentials/setup | Configuration Required | Use an approved Pathao merchant account and the current client ID and client secret flow. |
| Booking/AWB | Needs Verification | Confirm whether booking and airway-bill/consignment creation are enabled for this account. |
| Charges/COD | Needs Verification | Confirm charge calculation and COD options with the current provider flow. |
| Tracking/status sync | Needs Verification | Confirm which status updates are visible and how often they refresh. |
| Cancellation/returns/RTO | Needs Verification | Confirm cancellation, reverse pickup, return, and return-to-origin operations before promising them. |
| COD settlement vs customer payment confirmation | Partially Available | A COD amount is an instruction to collect. Courier settlement or delivery is not verified customer payment and must not automatically mark an order paid. |
| Failure/error handling | Needs Verification | Use the current provider response and support process; do not duplicate an ambiguous booking blindly. |

## Setup and observable behavior

After configuration, verify the connected merchant account, run a controlled test, and confirm the resulting booking and tracking state in AutoZeniq and Pathao. Exact service coverage, address rules, charges, milestones, labels, notifications, and return operations are **Needs Verification**.

## Related documents

- [Delivery and Logistics](../products/delivery-logistics.md)
- [Order Management](../products/order-management.md)
