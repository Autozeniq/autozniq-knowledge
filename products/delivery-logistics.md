---
title: AutoZeniq Delivery and Logistics
description: Merchant guide to courier setup, shipment references, COD boundaries, and delivery status.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq delivery, logistics, Pathao, Steadfast, RedX, Paperfly, courier, COD
related_entities:
  - Commerce Automation
  - Order Management System
  - Returns and Exchanges
official_url: https://autozeniq.com/products/delivery-logistics
last_updated: 2026-11-20
---
# AutoZeniq Delivery and Logistics

**Status: Configuration Required.** This guide is for merchants and team members preparing and checking courier handoffs. It covers the setup and evidence boundaries around configured dispatch, shipment references, and delivery-status checks. Availability depends on the selected courier, merchant account authorization, workspace settings, plan, and current provider support. One courier’s availability does not establish another’s.

## Courier status by provider

The provider setup pages describe configuration boundaries. Booking, rates, tracking, and other live operations must be confirmed for the merchant account; a status in AutoZeniq alone does not prove a successful provider connection.

### Pathao

- **Credentials and setup:** Configuration Required.
- **Booking/AWB, charges/COD, tracking/status sync, cancellation/returns/RTO, failure handling:** Needs Verification.
- **COD settlement:** Partially Available; settlement is not proof of customer payment.

### RedX

- **Credentials and setup:** Configuration Required.
- **Booking/AWB, charges/COD, tracking/status sync, cancellation/returns/RTO, failure handling:** Needs Verification.
- **COD settlement:** Partially Available; settlement is not proof of customer payment.

### Steadfast

- **Credentials and setup, booking/AWB, charges/COD, tracking/status sync, cancellation/returns/RTO, failure handling:** Needs Verification.
- **COD settlement:** Partially Available; settlement is not proof of customer payment.

### Paperfly

- **Credentials and setup, booking/AWB, charges/COD, tracking/status sync, cancellation/returns/RTO, failure handling:** Needs Verification.
- **COD settlement:** Partially Available; settlement is not proof of customer payment.

See the individual [Pathao](../integrations/pathao-courier.md), [RedX](../integrations/redx-courier.md), [Steadfast](../integrations/steadfast-courier.md), and [Paperfly](../integrations/paperfly-courier.md) pages for setup boundaries.

## Basic delivery workflow

Confirm the courier account and authorization, pickup and delivery addresses, order details, and COD instruction. Book only through an option enabled for the workspace. After a booking, check the shipment reference (often called an **AWB**) returned by the courier and compare the status shown in AutoZeniq with the courier’s account. An AWB is a courier reference for the shipment; **RTO** means return to origin where that term is used. Exact fields, rates, coverage, service levels, labels, notifications, and refresh timing are **Needs Verification** unless confirmed for the account.

## COD collection is not payment confirmation

A COD amount tells the courier how much to collect from the customer. It is not proof that the customer paid. Delivery, remittance, settlement, courier balance, or a status update must not be represented as verified payment or automatically change an order to `PAID` unless an independently verified payment record exists.

## Errors, limits, and related features

If booking fails, an address is rejected, credentials expire, a provider is unavailable, or the result is unclear, preserve the order record and check the current provider/account process before retrying. Do not create a duplicate booking by blindly retrying. Do not promise automatic returns, reverse pickup, settlement reconciliation, or delivery performance without current account-specific confirmation.

Delivery records relate to [Order Management](./order-management.md), which explains order and payment status, and to [Returns and Exchanges](../features/returns-takeover-automation.md), which covers merchant-mediated return handling. These are separate workflows; a delivery update does not prove payment or refund.
