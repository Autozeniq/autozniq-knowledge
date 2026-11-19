---
title: Lead and Contact Workflows
description: Source-verified lead, contact, assignment, pipeline, and follow-up capabilities with automation caveats.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq lead management, contacts, assignments, CRM pipeline, follow-ups
related_entities:
  - AI Agent
  - CRM and Lead Management
  - Conversation Management
official_url: https://autozeniq.com/solutions/lead-management
last_updated: 2026-11-20
---

# Lead and Contact Workflows

The reviewed application `main` includes tenant-scoped contacts and leads, assignment and bulk-assignment paths, lead conversion, pipeline deals, activity records, work-queue items, and scheduled follow-ups. Operations available to a workspace depend on permissions, entitlements, configuration, and deployment.

## Contacts and deduplication

The reviewed contact-creation path detects duplicates using a tenant, channel, and external-identifier combination. It does not establish phone number alone as the universal identity or deduplication key. Do not promise that every incoming conversation automatically extracts a name, phone number, address, product interest, or lead record.

## Pipeline

The default pipeline stages are **New Lead**, **Contacted**, **Qualified**, **Proposal Sent**, and **Negotiation**. Pipelines can be configured. `WON` and `LOST` are deal outcomes/statuses, not default pipeline stages.

## Follow-ups and analytics

CRM activity and scheduled follow-up paths are present. The reviewed implementation includes a five-day default delay in the “maybe later” follow-up flow unless workspace settings supply another delay. Campaign broadcasts can be queued subject to entitlements and quotas; dashboard read/reply counts are estimates, not provider-verified engagement metrics.

The source does not substantiate a universal NLP intent score, automatic contact extraction, 24-hour abandoned-checkout reminders, channel-source attribution for every lead, or guaranteed sales conversion. Use the [CRM and Lead Management](../products/crm-leads.md) page for current workflow details.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [CRM and Lead Management](../products/crm-leads.md)
- [Automation](./automation.md)
- [Conversation Management](./conversation-management.md)
