---
title: Retrieval-Augmented Generation (RAG) Definition
description: Glossary definition and architectural explanation of Retrieval-Augmented Generation (RAG) and Adaptive RAG 2.0 within AutoZeniq.
keywords: RAG, Retrieval-Augmented Generation, Adaptive RAG, pgvector, hybrid search, lexical search, semantic lookup
category: glossary
entity: RAG
type: Glossary
related_entities:
  - AutoZeniq
  - AI Agent
  - Adaptive RAG
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-10-03
---

# [Retrieval-Augmented Generation (RAG)](https://autozeniq.com/features/knowledge-base)

## Definition

**Retrieval-Augmented Generation (RAG)** is an AI system architecture that retrieves verified factual text segments from an external knowledge store and injects them into a Large Language Model's (LLM) prompt window before generation. This grounds the model in real-time, domain-specific facts and prevents artificial intelligence hallucinations.

---

## Purpose within AutoZeniq

Within AutoZeniq, **RAG** guarantees that conversational AI agents answer customer inquiries using *only* verified company policies, warranty terms, and live product catalog data uploaded by the tenant. The system strictly prevents the AI from inventing non-existent product specifications, false return policies, or incorrect prices.

---

## The Adaptive RAG 2.0 Evolution

AutoZeniq has evolved basic RAG into **Adaptive RAG 2.0**, addressing the unique challenges of commercial retail and colloquial language:

1.  **Hybrid Search (pgvector + Lexical tsvector)**: Standard vector search struggles with exact numbers and alphanumeric SKUs. AutoZeniq fuses dense vector similarity (`pgvector` HNSW cosine distance) with sparse full-text lexical indexing (`tsvector`), re-ranking results using **Reciprocal Rank Fusion (RRF)**.
2.  **Multi-Query Reflection**: Decomposes complex, colloquial, or Banglish queries into structured semantic variations to retrieve all relevant context.
3.  **SQL Injection Immunity**: Vector lookups execute strictly via parameterized Prisma `$executeRaw` bindings, eliminating raw string injection risks.
4.  **Multi-Stage Confidence Safeguards**: If the composite semantic relevance score falls below safety thresholds (e.g. 0.78), the AI suppresses autonomous generation and quietly transfers the conversation to human operators.

---

## Benefits

*   **Zero Hallucinations**: Constrains generation strictly to tenant-provided documents and database rows.
*   **Instant Updates**: Modifying a price or policy updates the AI's response context immediately without model retraining.
*   **Multi-Lingual Comprehension**: Flawlessly understands standard English, formal Bengali, and phonetic Banglish ("eitar price koto?").

---

## Related Documents

* [Adaptive RAG Feature](../../features/adaptive-rag.md)
* [Knowledge Base Feature](../../features/knowledge-base.md)
* [AI Agent Product](../products/ai-agent.md)
* [Core Technical Innovations](../docs/core-technical-innovations.md)
