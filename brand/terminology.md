---
title: AutoZeniq Platform Terminology
description: Status-qualified reference for product, billing, AI, and integration terms used in AutoZeniq documentation.
entity: AutoZeniq
type: Brand
category: company
keywords: AutoZeniq terminology, product glossary, platform vocabulary, feature status
related_entities:
  - AI Agent
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
official_url: https://autozeniq.com/
last_updated: 2026-11-20
---

# AutoZeniq Platform Terminology

Use these definitions consistently when describing the product. A capability present in the application repository is not, by itself, proof of production deployment or general availability.

## Core terms

- **Workspace / tenant**: A merchant's scoped account area, members, records, settings, and entitlements.
- **Entitlement**: A plan, subscription, usage, add-on, or workspace-override rule that can permit or limit a product operation.
- **Order lifecycle status**: A validated operational state of an order, such as `CONFIRMED`, `SHIPPED`, or `DELIVERED`. It is not proof of payment.
- **Verified payment**: A payment credit recorded only after the applicable provider or other authorized verification path. A courier remittance record alone is not a verified customer payment.
- **COD remittance**: Funds reported or settled by a courier against a consignment. On the reviewed application `main`, customer COD collection credit is disabled; remittance must not be described as marking an order paid.
- **Staged storefront payment**: A checkout configuration that can use COD-only, advance-plus-COD, full online, or partial payment modes, subject to configured rules and provider verification.

## Product and technical terms

- **Store builder**: The tenant-facing tools for editing store settings, pages, navigation, previewing drafts, publishing, and managing versions. Custom-domain readiness depends on ownership, DNS, and TLS checks.
- **Google Sheets synchronization**: A scheduled and queued ingestion path that is primarily pull-oriented in the reviewed source. Dashboard connection checks and previews can be simulated; they are not proof of a live connection.
- **Adaptive retrieval / RAG**: A conversational retrieval approach that supplies relevant indexed context to response generation. Retrieval and guardrails can help constrain responses but do not guarantee correctness or eliminate hallucinations.
- **Workflow automation**: A graph-based workflow system with a limited set of connected triggers and executable actions. In the reviewed implementation, `order_placed` and `chat_keyword` are verified triggers and `notify_agent` is an executable action; unsupported actions fail closed.
- **Provider-dependent integration**: Source code for an adapter or connection path does not prove provider approval, valid credentials, enabled entitlements, or production operation.

## Messaging and support vocabulary

- **Shared inbox**: A workspace area for reviewing conversations, assigning work, replying, and using configured AI assistance. Availability depends on channel and provider setup.
- **AI Copilot suggestion**: A draft reply for an agent to review. It is not automatically sent merely because the feature exists.
- **Human takeover**: An agent control to pause or take over AI handling where the conversation and workspace support it.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Capabilities](../capabilities.md)
- [Product Overview](../products/overview.md)
- [System Architecture](../docs/system-architecture.md)
