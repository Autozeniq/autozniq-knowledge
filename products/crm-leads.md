---
title: AutoZeniq CRM and Lead Management
description: Current contact, lead, deal pipeline, follow-up, and campaign workflows with verified analytics limits.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq CRM, contacts, leads, sales pipeline, deals, follow-ups, campaigns
related_entities:
  - Lead Detection
  - Customer Support Automation
  - Order Management System
official_url: https://autozeniq.com/products/crm-leads
last_updated: 2026-11-20
---
# AutoZeniq CRM and Lead Management

The CRM codebase contains tenant-scoped contact and lead records, deal pipelines, activity and work-queue paths, scheduled follow-ups, and campaign broadcasting. Access and available operations depend on workspace permissions, plan entitlements, and configuration.

## Contacts and leads

Contacts support paginated search, lifecycle/VIP/tag filters, channel metadata, and related order, conversation, and deal context. The reviewed create path detects duplicates using a tenant/channel/external-identifier combination; it does not establish phone number as the sole primary deduplication key.

Lead tools support list/filter views, status/grade/notes/follow-up changes, assignment, bulk assignment, deal conversion, customer marking, reopening, and timeline events. Avoid claiming every conversation automatically creates or updates a lead unless the specific path is verified.

## Deals and pipeline

Deals can be created, filtered, updated, moved between valid stages, marked won/lost, and reopened, with timeline events. The current default pipeline stages are:

1. New Lead
2. Contacted
3. Qualified
4. Proposal Sent
5. Negotiation

`WON` and `LOST` are deal outcomes/statuses, not the default pipeline stages. The pipeline can be configured; do not present the default stages as the only possible configuration.

## Follow-ups and campaigns

CRM activities and delayed follow-ups are present. Scheduled follow-up records can be queued and written to the contact timeline; the default delay in the reviewed maybe-later flow is five days unless tenant settings provide another delay.

The campaigns area supports entitlement-guarded campaign creation, audience selection, quota checks, and staggered broadcast queueing. Counts shown as campaign reads/replies in the UI are calculated estimates from recipient counts, not verified provider engagement telemetry.

## Affiliate program status

The public affiliate program is currently closed: applications are not accepted, rates and payout terms are unset, and affiliate earning, approval, activation, and payout actions are disabled. The authenticated affiliate view is read-only. Do not publish commission rates, earnings estimates, or payout availability.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Lead Detection](../features/lead-detection.md)
- [Automation](../features/automation.md)
- [Pricing](../pricing.md)
