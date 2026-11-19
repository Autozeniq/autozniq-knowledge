---
title: AutoZeniq Delivery and Logistics
description: Courier booking, tracking, conditional auto-booking, fraud signals, and verified limits of COD settlement.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq delivery, logistics, Pathao, Steadfast, RedX, Paperfly, consignment, COD
related_entities:
  - Commerce Automation
  - Order Management System
  - Pathao Courier Integration
  - Steadfast Courier Integration
official_url: https://autozeniq.com/products/delivery-logistics
last_updated: 2026-11-20
---
# AutoZeniq Delivery and Logistics

The delivery module connects tenant orders with courier workflows. The reviewed application `main` contains adapters for Pathao, Paperfly, RedX, and Steadfast, plus consignment booking, bulk booking, tracking, public tracking, OTP, and courier webhook paths. Actual service availability depends on tenant entitlements, provider credentials, account approval, and deployment configuration.

## Booking and tracking

Eligible confirmed or processing orders can be submitted for consignment booking. Booking records use durable claims to reduce duplicate provider requests. If a provider result is ambiguous, the system blocks blind automatic retries and requires reconciliation. Conditional auto-booking depends on tenant settings and selected order/payment/risk triggers; it is not a blanket automatic-dispatch guarantee.

Provider status updates are checked against tenant/courier context and idempotency controls before processing. The dashboard contains consignment search/filtering, booking, tracking refresh, courier configuration, and settlement views. Do not promise every optional label, reverse-pickup, notification, or provider-specific operation without verifying its complete path.

## COD remittance is not payment verification

AutoZeniq records courier COD remittances and settlement references against consignments. These records are distinct from verified customer payment credit. **The reviewed default-branch code explicitly disables customer COD collection credit** because current adapters do not independently verify the required amount, currency, and provider reference. A courier settlement must not be described as proof of customer payment or as an automatic order-to-`PAID` update.

## Fraud and analytics

The fraud service can produce a bounded risk score and factors using hashed phone identifiers, anonymized platform return-to-origin history, and tenant-local order history. Merchants may configure prevention and thresholds. This does not guarantee that fraud or returns are prevented.

Some super-admin delivery and returns/fraud monitoring surfaces are present. The merchant delivery analytics page currently contains sample courier, RTO, cost, and SLA data; it must not be presented as live tenant performance. The backend exposes narrower live delivery/RTO aggregates.

## Important boundaries

- Courier booking/tracking code does not prove a provider account is connected or operational in production.
- Remittance records do not establish verified COD customer payment.
- Do not claim zero manual dispatch, automatic settlement reconciliation, duplicate-free retries after ambiguous outcomes, or quantified delivery improvements without evidence.
- Distinguish shipped application code from deployment and provider availability.

## Related documents

- [Order Management](./order-management.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Pathao integration](../integrations/pathao-courier.md)
- [Steadfast integration](../integrations/steadfast-courier.md)
- [Security](../security.md)
