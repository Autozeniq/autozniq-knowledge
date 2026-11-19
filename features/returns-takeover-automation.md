---
title: Returns, Exchanges, and Human Takeover
description: Merchant-managed return/exchange requests, eligibility checks, inventory handling, and AI escalation boundaries.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq returns, exchange, human takeover, return request, order validation, support escalation
related_entities:
  - AI Agent
  - Order Management System
  - Customer Support Automation
official_url: https://autozeniq.com/features/returns-takeover
last_updated: 2026-11-20
---
# Returns, Exchanges, and Human Takeover

The application supports merchant-mediated return and exchange management for delivered orders. Staff can review requests, approve or reject them, and handle eligible returned quantities or exchange stock through the order workflow. A customer self-service return-submission flow was not verified in the reviewed `main` source.

## Return and exchange boundaries

Return approval, inventory restocking, courier reverse pickup, order status changes, and money refunds are separate actions. Eligible approved return quantities may be restocked; exchange flow can check replacement stock. The reviewed implementation does not establish automatic refund transfers or universal courier reverse-pickup booking.

Do not promise a fixed return window, automatic AI confirmation flow, or return eligibility rule across tenants unless a current merchant policy and active workflow confirm it. A return record does not prove that a refund was issued.

## Human takeover

AI reply paths can be paused or handed off for human handling. Selected complaint and escalation paths can flag an interaction for attention; escalation severity, notifications, and AI behavior depend on tenant settings and enabled channels. Do not claim every legal, payment, or emotional-language case is always detected or reaches a senior team instantly.

## Related documents

- [Order Management](../products/order-management.md)
- [AI Auto-Reply](./ai-auto-reply.md)
- [Automation](./automation.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
