---
title: AutoZeniq Workflow Automation
description: Tenant workflow graph creation, connected triggers, executable notification action, and current limitations.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq automation, workflows, triggers, notification, order event, chat keyword
related_entities:
  - Customer Support Automation
  - Commerce Automation
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features/workflow-builder
last_updated: 2026-11-20
---
# AutoZeniq Workflow Automation

The backend contains tenant-scoped workflow graph creation and updates, validation, publishing, execution records, queued processing, execution leases, idempotent notifications, and limited recovery. A saved graph or UI node does not mean its action is connected or executable.

## Connected triggers and action

In the reviewed `main` path, `order_placed` is connected to a created order event and `chat_keyword` to persisted inbound customer text. `notify_agent` is the executable workflow action found in the processor; it creates a tenant-scoped in-app notification.

`cart_abandoned` is listed but lacks a safe automatic event emitter in the reviewed code. It must be treated as a manual bridge, not an automatic event trigger. `send_whatsapp_template` and `apply_coupon` are present in the action catalog but fail closed; they do not execute their named effects.

## Reliability and limits

Workflow graphs are validated and queued under tenant scope. Execution uses persisted state/leases and idempotency controls for notification actions. Recovery is deliberately limited to notification-only graphs; do not promise arbitrary action retries or exactly-once side effects.

Do not advertise courier booking, stock reservation, lead tagging, arbitrary webhooks, outbound WhatsApp template delivery, coupon application, or other design-only nodes as live workflow actions. Workflow entitlements, usage limits, configuration, and provider connections still apply.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Order Management](../products/order-management.md)
- [Delivery and Logistics](../products/delivery-logistics.md)
- [CRM and Leads](../products/crm-leads.md)
