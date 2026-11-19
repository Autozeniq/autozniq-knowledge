---
title: Pathao Courier Integration Status
description: Source-verified Pathao adapter scope, configuration dependencies, and COD payment verification boundary.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Pathao courier integration, consignment booking, tracking, COD, order fulfillment
related_entities:
  - Delivery Logistics
  - Order Management System
  - Current Feature Inventory
official_url: https://autozeniq.com/integrations/pathao
last_updated: 2026-11-20
---
# Pathao Courier Integration

The reviewed application `main` includes a Pathao courier adapter for consignment booking and provider status/tracking workflows. Use depends on tenant credentials, provider account permissions, configuration, and deployment. Code availability does not prove the merchant's Pathao account is connected or production-ready.

## COD boundary

A booking can send a configured amount-to-collect to the courier. That is an instruction to collect, not evidence that Pathao collected or remitted the money. The reviewed application explicitly disables verified customer COD credit; a Pathao delivery or settlement event must not be represented as proof that the order is paid.

## Important limits

- Exact credential fields, booking options, rate calculations, service levels, city coverage, tracking milestones, and current provider contract terms should be confirmed in the active dashboard and Pathao account.
- Do not claim automatic reverse pickup, delivery-rate calculation, SMS/WhatsApp notification, or settlement reconciliation unless separately verified for the specific path.
- If a booking result is ambiguous, the application requires reconciliation rather than a blind duplicate booking.

## Related documents

- [Delivery and Logistics](../products/delivery-logistics.md)
- [Order Management](../products/order-management.md)
- [Billing and Entitlements](../features/billing-entitlements.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
