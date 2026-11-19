---
title: AutoZeniq Adaptive Retrieval and RAG
description: Source-verified conversational retrieval, query adaptation, reranking, context handling, and confidence safeguards.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq RAG, hybrid search, PostgreSQL vector search, reranking, query rewriting, retrieval
related_entities:
  - RAG
  - AI Agent
  - Knowledge Base Feature
official_url: https://autozeniq.com/features/adaptive-rag
last_updated: 2026-11-20
---
# Adaptive Retrieval and RAG

AutoZeniq's conversational retrieval code combines semantic vector search with PostgreSQL keyword search. Adaptive steps can cache retrieval results, rewrite or expand queries, route by query type, rerank sources, expand parent context, apply configured thresholds, and detect possible conflicts among retrieved material.

## How it is used

When the AI reply flow has eligible indexed context, retrieval supplies context to response generation. Confidence/safety paths can constrain or defer uncertain responses. Availability and behavior depend on model/provider configuration, knowledge sources, entitlements, and tenant AI settings. AI Copilot suggestions are drafts; the existence of AI automation paths does not mean every reply is sent automatically.

## What not to infer

Source code does not substantiate zero hallucinations, a fixed 0.78 threshold across tenants, sub-800ms latency, universal source citations, guaranteed provider failover, specific current model rankings, or quantified savings/accuracy improvements. Do not claim that every product price or Google Sheet change is instantly indexed.

## Related documents

- [Knowledge Base](./knowledge-base.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [AI Agent](../products/ai-agent.md)
- [Google Sheets Synchronization](./google-sheets-sync.md)
