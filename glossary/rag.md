---
title: Retrieval-Augmented Generation (RAG)
description: Plain-language definition of RAG and the verified retrieval features and limits in AutoZeniq.
keywords: RAG, Retrieval-Augmented Generation, AutoZeniq retrieval, semantic search, keyword search
category: glossary
entity: RAG
type: Glossary
related_entities:
  - AutoZeniq
  - AI Agent
  - Adaptive RAG
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-11-20
---

# Retrieval-Augmented Generation (RAG)

## Definition

**Retrieval-augmented generation (RAG)** is an approach in which a system retrieves relevant information from a knowledge source and supplies it as context to a language model. RAG can help an answer use current, task-specific information; it does not guarantee factual correctness or prevent every hallucination.

## RAG in AutoZeniq

The reviewed application `main` includes tenant-authorized ingestion for supported document and data formats, asynchronous parsing and indexing, and conversational retrieval that combines semantic vector search with PostgreSQL keyword search. Adaptive retrieval paths can cache results, rewrite or expand queries, route by query type, rerank sources, expand parent context, apply thresholds, and detect possible conflicts.

Availability and results depend on what has been ingested, permissions, model/provider configuration, workspace settings, and deployment. The reviewed source does not establish a URL crawler, universal citations, a fixed confidence threshold for all tenants, zero hallucinations, fixed latency, or quantified accuracy/cost improvements.

For details see [Adaptive Retrieval and RAG](../features/adaptive-rag.md) and the [Current Feature Inventory](../docs/current-feature-inventory.md).
