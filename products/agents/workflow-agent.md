---
title: Workflow Automation
description: Merchant-facing overview of supported workflow automation and its limits.
entity: AutoZeniq
type: Product Reference
category: product
keywords: AutoZeniq workflow automation, triggers, actions, rules
related_entities:
  - Order Management System
  - Delivery Logistics
  - Current Feature Inventory
last_updated: 2026-11-20
---
# Workflow Automation
AutoZeniq may support rules that respond to selected events with selected actions. **Status: Partially Available.** Use only the triggers and actions shown as available in your workspace.

## Availability boundaries
- **Workflow setup and publishing:** **Status: Needs Verification.**
- **Event triggers:** **Status: Needs Verification.** Confirm the exact event list.
- **Actions:** **Status: Needs Verification.** Do not assume a workflow can book couriers, change payment status, reserve stock, send messages, or apply discounts unless the current product documentation explicitly says so.
- **Autonomous commerce agent:** **Status: Not Available.** A workflow is not a general-purpose agent.

## Troubleshooting
Check that the workflow is enabled, the source event occurred, the workspace has the required plan access, and the target connection is active. Test with a low-risk record before applying a workflow broadly.
