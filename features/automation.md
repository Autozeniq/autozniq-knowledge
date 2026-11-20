---
title: AutoZeniq Workflow Automation
description: Merchant-facing guide to workflow availability, setup requirements, and supported boundaries.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq automation, workflows, triggers, notifications, order events, chat keywords
related_entities:
  - Customer Support Automation
  - Commerce Automation
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features/workflow-builder
last_updated: 2026-11-20
---
# AutoZeniq Workflow Automation

**Status: Partially Available.** Eligible workspaces can create and publish workflows using the triggers and actions shown as enabled. Availability depends on plan entitlement, workspace permissions, connected providers, and configuration.

## Supported workflow scope

The documented workflow scope includes two triggers: an order being placed and an incoming chat message matching a configured keyword. The supported action is notifying a team agent. Confirm that these options are enabled in your workspace before relying on them.

Cart-abandonment triggers, WhatsApp message templates, coupon application, and arbitrary actions are **Not Available** in the documented workflow scope. Do not assume other events or outcomes are active just because they appear in a selector or roadmap discussion.

## Prerequisites

Use an eligible plan, grant the workflow creator the required workspace role, connect any required provider, and test the workflow with a non-production scenario before relying on it. Publishing a workflow does not prove that its event source or every selected action is configured.

## Reliability limits

A workflow may be delayed or skipped when an event is not received, a provider is unavailable, a condition is not met, or an entitlement is exhausted. Do not promise arbitrary retries or exactly-once external side effects.

## Troubleshooting

Check that the workflow is published, the selected trigger is supported, the provider is connected, and the event appears in the workspace. Review the workflow run result and correct validation errors before republishing. Contact support with the workflow name, event time, and displayed error if it still does not run.

## Related documents

- [CRM and Lead Management](../products/crm-leads.md)
- [Current capabilities](../capabilities.md)
