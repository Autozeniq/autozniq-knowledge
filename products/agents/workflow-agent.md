---
title: Workflow Automation
description: Verified workflow graph, connected triggers, executable action, and fail-closed limitations; not an autonomous commerce agent.
entity: AutoZeniq
type: Product Reference
category: product
keywords: AutoZeniq workflow, automation triggers, notify agent, order placed, chat keyword
related_entities:
  - AutoZeniq AI Agent
  - Order Management System
  - Delivery Logistics
last_updated: 2026-11-20
---

# Workflow Automation

The reviewed application `main` includes tenant-scoped workflow graphs that can be saved, validated, published, queued, leased, and recovered. This is a limited workflow builder, not evidence of a language-model agent that can execute arbitrary commerce operations.

## Connected behavior

The verified connected triggers are `order_placed` and `chat_keyword`. `notify_agent` is the executable action found in the reviewed path. `send_whatsapp_template` and `apply_coupon` fail closed, and `cart_abandoned` lacks a safe automatic event emitter in the reviewed code and is a manual bridge only.

## Availability and limits

Do not describe courier booking, lead tagging, stock reservation, arbitrary webhooks, WhatsApp template sending, coupon application, or other design-only nodes as available workflow actions. Workflow publication, queue processing, entitlements, configuration, and deployment affect use. Safe recovery is limited to notification-only graphs.

For the full source-qualified list, see [Automation](../../features/automation.md) and the [Current Feature Inventory](../../docs/current-feature-inventory.md).
