---
title: AutoZeniq Core Technical Capabilities
description: Source-verified technical capabilities across AI, commerce, integrations, data, and security, with current status caveats.
entity: AutoZeniq
type: Documentation
category: docs
keywords: AutoZeniq technical capabilities, adaptive RAG, commerce, workflows, data integration, security
related_entities:
  - System Architecture
  - Capabilities
  - Current Feature Inventory
  - Order Management System
official_url: https://autozeniq.com/docs/technical-innovations
last_updated: 2026-11-20
---
# AutoZeniq Core Technical Capabilities

AutoZeniq's reviewed application `main` contains a broad multi-tenant platform spanning messaging, AI, commerce, CRM, integrations, billing, and operations. The capabilities below describe source code, not independently verified deployment, provider approval, production usage, or measured customer outcomes. See the [Current Feature Inventory](./current-feature-inventory.md) for detailed status and caveats.

## Conversational AI and retrieval

- The shared inbox supports conversation history, human replies, assignment, AI pause/takeover/resume, and selected live updates.
- AI Copilot can create reply suggestions; those are drafts, not automatically sent messages.
- Knowledge ingestion supports PDF, DOC/DOCX, CSV, JSON, and plain text. Retrieval combines vector and PostgreSQL keyword search and includes adaptive query/reranking/context steps.
- Multimodal voice/image processing paths exist, but do not claim universal media support, recognition accuracy, or cost savings without deployment and benchmark evidence.

## Commerce and delivery

- Tenant-scoped catalog, inventory, storefront, checkout, orders, returns/exchanges, and courier adapter paths are present.
- Order lifecycle validation includes confirmation, processing, courier and delivery states, returns, RTO, and exchanges.
- Tenant storefront payment modes include COD-only, advance-plus-COD, full online, and partial payment. COD collection credit is disabled until verified collection evidence is available; courier remittance is not proof of customer payment.
- Courier booking and tracking depend on tenant credentials and provider configuration; ambiguous booking results are held for reconciliation.

## CRM and workflow automation

- CRM includes contacts, leads, deals, activity and follow-up paths, and campaign broadcast flows, subject to entitlements and quota.
- Default deal pipeline stages are New Lead, Contacted, Qualified, Proposal Sent, and Negotiation; WON/LOST are deal outcomes.
- Workflow graphs and queue processing are implemented, but only `order_placed` and `chat_keyword` triggers and `notify_agent` action were verified as connected. Other catalog entries fail closed or lack a safe emitter.

## Integrations and platform administration

- Provider connection paths exist for supported messaging channels. Actual channel access depends on OAuth/account permissions, configuration, and deployment.
- The scoped Public API covers selected conversations, messages, customers, orders, knowledge, and webhook endpoint management. Published Node/Python SDK packages were not verified.
- Google Sheets synchronization is scheduled/queued and primarily pull-oriented; parts of the dashboard wizard simulate connection and preview.
- Tenant/platform administration, entitlements, audit views, and selected operational monitoring exist, but some screens contain sample values or partial paths.

## No unsupported outcomes

The reviewed repository does not substantiate claims such as zero hallucinations, 97% image matching, 95% inference savings, sub-second global responses, zero overselling/cancellations, quantified conversion uplift, unlimited scale, complete compliance certification, or guaranteed delivery. Publish outcome metrics only with current measurement evidence.

## Related documents

- [Current Feature Inventory](./current-feature-inventory.md)
- [System Architecture](./system-architecture.md)
- [Security and Privacy](../security.md)
- [Pricing](../pricing.md)
- [Products Overview](../products/overview.md)
