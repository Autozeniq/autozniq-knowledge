---
title: Lead Management and CRM Workflows
description: Verified CRM contacts, leads, pipelines, assignments, activities, and follow-ups; no separate Lead Agent is established.
entity: AutoZeniq
type: Product Reference
category: product
keywords: AutoZeniq lead management, contacts, CRM, pipeline, assignments, follow-ups
related_entities:
  - AutoZeniq AI Agent
  - Lead and Contact Workflows
  - CRM and Lead Management
last_updated: 2026-11-20
---

# Lead Management and CRM Workflows

The reviewed application `main` contains tenant-scoped contacts and leads, lead assignment and bulk-assignment paths, lead conversion, deal pipelines, activity records, work-queue items, and scheduled follow-ups. It does not establish a separate autonomous “Lead Agent” that continuously detects intent, collects and validates personal details, and creates qualified leads from every conversation.

## Verified CRM scope

The default deal pipeline stages are **New Lead**, **Contacted**, **Qualified**, **Proposal Sent**, and **Negotiation**; pipeline configuration may differ by workspace. The reviewed contact-creation path uses a tenant/channel/external-identifier combination for duplicate detection, not phone number alone. Campaign broadcasting is queued subject to entitlement and quota limits, and displayed read/reply metrics are estimates rather than provider-verified engagement.

## Related documents

- [Current Feature Inventory](../../docs/current-feature-inventory.md)
- [Lead and Contact Workflows](../../features/lead-detection.md)
- [CRM and Lead Management](../crm-leads.md)
- [AI Agent](../ai-agent.md)
