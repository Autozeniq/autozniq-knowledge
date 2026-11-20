---
title: AutoZeniq Workflow Automation
description: Merchant guide to supported workflow triggers, team notifications, setup, and limits.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq automation, workflows, triggers, notifications, order events, chat keywords
related_entities:
  - Customer Support Automation
  - Commerce Automation
  - Order Management System
  - Unified Inbox
official_url: https://autozeniq.com/features/workflow-builder
last_updated: 2026-11-20
---
# AutoZeniq Workflow Automation

**Status: Partially Available.** Workflow Automation helps merchant teams notify a team agent when a supported order event occurs or an incoming chat matches a configured keyword. It is intended for workspace teams that coordinate customer support and order follow-up. Availability depends on plan access, workspace permissions, event or chat connection, and configuration.

## Supported workflow scope

The documented workflow scope includes two triggers: an order being placed and an incoming chat message matching a configured keyword. The supported action is notifying a team agent. Confirm that these options are enabled in your workspace; do not assume that an event or action is active just because it appears in a selector or roadmap discussion.

Cart-abandonment triggers, WhatsApp message templates, coupon application, and arbitrary actions are **Not Available** in the documented workflow scope.

## Setup and basic flow

Use a workspace role that can create workflows, and confirm plan access and any required order event or connected chat source. In the visual workflow, choose a supported trigger, set a keyword for a chat trigger if needed, and select **Notify agent**. Test with a non-production scenario, check the result, and publish only after the expected notification is confirmed. Publishing does not prove that every event source or action is configured.

## Reliability limits and troubleshooting

A workflow may be delayed or skipped if an event is not received, a source is unavailable, a condition is not met, or workspace limits are reached. Do not assume that every action will retry or that external effects happen only once.

If a workflow does not run, check that it is published, the selected trigger is supported, the event or chat source is connected, and the expected event appears in the workspace. Review the run result and correct any validation errors before testing again. Do not rely on it for payment marking or other consequential actions unless those actions are explicitly enabled and verified.

## Related features

Order triggers relate to [Order Management](../products/order-management.md); chat triggers and agent notifications relate to the [Unified Inbox](./unified-inbox.md). [CRM and Lead Management](../products/crm-leads.md) explains related customer records, but a workflow notification does not itself guarantee a complete lead record.
