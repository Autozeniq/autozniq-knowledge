---
title: Steadfast Courier Integration Status
description: Source-verified Steadfast adapter scope and the distinction between COD instructions, remittance, and verified payment.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Steadfast courier, API integration, consignment, tracking, COD, payment verification
related_entities:
  - Delivery Logistics
  - Order Management System
  - Current Feature Inventory
official_url: https://autozeniq.com/integrations/steadfast
last_updated: 2026-11-20
---
# Steadfast Courier Integration

The reviewed application `main` contains a Steadfast courier adapter and delivery flows for booking and tracking. A working live connection depends on tenant credentials, merchant account approval, provider behavior, and deployment configuration.

## COD payment boundary

The order's COD amount may be sent as a collection instruction. A courier delivery status, remittance statement, settlement reference, or courier balance is not independently verified customer payment evidence. The current default-branch application explicitly disables customer COD collection credit. **Steadfast delivery must not automatically be documented as marking an order `PAID`.**

## Configuration and availability

Use the active dashboard and the merchant's Steadfast portal for current supported credential and account setup details. Do not rely on historical credential screenshots, API payload examples, service-level claims, or fixed booking speeds as a current integration contract.

Actual delivery milestones and supported operations may differ by provider account and API. A provider adapter in source does not establish a connection or active production integration for any tenant.

## Related documents

- [Delivery and Logistics](../products/delivery-logistics.md)
- [Order Management](../products/order-management.md)
- [Billing and Entitlements](../features/billing-entitlements.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
