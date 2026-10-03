---
title: Business Workflow Automation Features
description: Features of the AutoZeniq Rule Engine, including conditional workflows, courier auto-booking, and database actions.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq automation, Rule Engine, workflow automation, triggers, courier auto-booking, database connector, conditional logic
related_entities:
  - Customer Support Automation
  - Commerce Automation
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/solutions/sales-automation
last_updated: 2026-10-03
---

# [Business Workflow Automation Features](https://autozeniq.com/solutions/sales-automation)

## Overview

The AutoZeniq Business Workflow Automation module allows merchants to build custom, event-driven business rules. Through the platform's visual **[Rule Engine / Workflow Builder](https://autozeniq.com/features/workflow-builder)**, users combine deterministic triggers with conditional logic to execute automated commercial actions—such as tagging high-intent leads, reserving product stock, auto-booking courier consignments with **Pathao** or **Steadfast**, or emitting outbound webhooks.

---

## Technical Architecture

This module runs a centralized event-driven rule evaluator:

```mermaid
graph TD
    A[Inbound Event: Message / Order / Cart] --> B[Rule Evaluator Hook]
    B --> C[AST Logic Engine (AND / OR Evaluation)]
    C -->|Condition Met| D[Action Dispatcher (BullMQ Queue)]
    D --> E1[Tag Lead in CRM]
    D --> E2[Create Order in OMS]
    D --> E3[Auto-Book Consignment via Courier Registry]
    D --> E4[Trigger Outbound HMAC Webhook]
```

### Technical Execution Details

1.  **Event Hook Ingestion**: When messages, orders, or cart updates occur, transaction hooks fire events to `RuleEngineService`.
2.  **AST Evaluation (Abstract Syntax Tree)**: Compiles user rules into logical conditions containing inputs (`message.content`, `contact.tags`, `order.status`, `delivery.zone`, `time.current`).
3.  **Action Dispatcher (BullMQ)**: Executes actions asynchronously through Redis BullMQ worker queues to guarantee execution and prevent API thread blocking.

---

## Core Operational Actions

*   **Courier Auto-Booking**: When an order transitions to `CONFIRMED`, automatically invokes `auto-booking.service.ts` to generate a live consignment with Pathao, Steadfast, RedX, or Paperfly.
*   **Lead Intent Scoring & Pipeline Movement**: Detects buyer inquiries, calculates Intent Scores, and pushes deals to the `QUALIFIED` stage on the visual Kanban board.
*   **Inventory Stock Alerts**: Monitors inventory levels; when variant stock falls below safety thresholds, automatically silences promotion rules and notifies the merchant.
*   **Urgent Takeover Escalation**: Detects customer frustration, dispute terms, or refund demands, immediately bypassing the AI agent and alerting human operators via push notifications.
*   **Google Sheets Sync Trigger**: Triggers automated catalog polling when high-volume campaigns are launched.

---

## Related Documents

* [Order Management System](../products/order-management.md)
* [Delivery & Logistics Automation](../products/delivery-logistics.md)
* [CRM & Lead Pipeline](../products/crm-leads.md)
* [Conversation Management](./conversation-management.md)
* [Adaptive RAG Feature](./adaptive-rag.md)
