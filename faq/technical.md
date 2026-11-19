---
title: AutoZeniq Technical FAQ
description: Current architecture, data, API, privacy, and security facts with evidence-based limits.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq technical FAQ, PostgreSQL, RAG, security, tenant access, privacy, queue
related_entities:
  - Security and Privacy
  - System Architecture
  - Current Feature Inventory
official_url: https://autozeniq.com/faq
last_updated: 2026-11-20
---
# AutoZeniq Technical FAQ

## What is the application architecture?
The reviewed repository contains a modular NestJS backend, a Next.js merchant/public frontend, and a separate Next.js storefront runtime. PostgreSQL/Prisma backs application records and retrieval; Redis supports selected cache and queue paths. Queue processors run within the backend process in the reviewed Compose topology; a separate worker service was not established.

## How does knowledge retrieval work?
The knowledge service supports PDF, DOC/DOCX, CSV, JSON, and plain-text ingestion. Retrieval combines vector and PostgreSQL keyword search with adaptive query, reranking, and context steps. This does not guarantee correct answers, universal citations, fixed latency, or zero hallucinations.

## Are all tables/queries universally tenant-isolated?
Current authenticated routes use current account and tenant-membership/role checks, and many services scope records by tenant. The source review did not establish universal isolation for every query/table, so avoid an absolute guarantee.

## How are credentials and tracking protected?
Integration and tracking credentials use authenticated encryption where enabled. Production config validation rejects missing or weak required secrets. Store tracking uses purpose-separated consent, suppresses pending events after revocation, quarantines legacy records without consent identity, and applies a 90-day tracking retention boundary. These details should not be generalized to all data categories.

## Does AutoZeniq have a security certification?
No certification or audit attestation is established by the reviewed application repository. Do not claim SOC 2, ISO, HIPAA, penetration-test completion, or a universal TLS/rate-limit standard without separate evidence.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [System Architecture](../docs/system-architecture.md)
- [Security and Privacy](../security.md)
