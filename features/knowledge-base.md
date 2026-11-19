---
title: AutoZeniq Knowledge Base and Retrieval
description: Supported document ingestion, asynchronous indexing, tenant-scoped hybrid retrieval, and current feature boundaries.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq knowledge base, RAG, document ingestion, vector search, PostgreSQL, hybrid retrieval
related_entities:
  - RAG
  - Adaptive RAG
  - Google Sheets Synchronization
  - AI Agent
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-11-20
---
# Knowledge Base and Retrieval

The knowledge service lets a workspace upload supported files and index content for conversational retrieval. The reviewed file paths include PDF, DOC/DOCX, CSV, JSON, and plain text. Ingestion and embedding/indexing are asynchronous; search combines semantic vector retrieval with PostgreSQL keyword search.

## Retrieval features

Conversational Adaptive RAG can cache retrieval results, rewrite or expand queries, route by query type, rerank retrieved content, expand parent context, apply confidence thresholds, and detect potential source conflicts. These are retrieval/generation safeguards, not a guarantee that every response is correct or citation-bearing.

## Boundaries

- A recursive website URL crawler, a complete Q&A/chunk editor, and a live knowledge-gap API were not verified in the reviewed `main` implementation.
- Universal citation display, fixed indexing times, zero hallucinations, and measured accuracy or cost improvements are not supported claims.
- Google Sheets import is a separate, partially integrated path; the dashboard wizard includes simulated connection and preview states.
- Exact source availability depends on workspace authorization, processing success, entitlements, and deployment configuration.

## Related documents

- [Adaptive RAG](./adaptive-rag.md)
- [Google Sheets Synchronization](./google-sheets-sync.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [AI Agent](../products/ai-agent.md)
