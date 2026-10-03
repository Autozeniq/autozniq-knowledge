---
title: Knowledge Base & RAG Indexing Feature
description: Detailed features of the AutoZeniq RAG Knowledge Base, document parsing, website crawling, hybrid search, and pgvector database indexing.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq knowledge base, RAG, document ingestion, vector database, pgvector, crawler, text chunking, hybrid search, parameterized SQL
related_entities:
  - RAG
  - Terminology
  - Adaptive RAG
  - Google Sheets Synchronization
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-10-03
---

# [Knowledge Base & RAG Indexing Feature](https://autozeniq.com/features/knowledge-base)

## Overview

The AutoZeniq **Knowledge Base** is the centralized data ingestion and retrieval workspace that grounds conversational AI agents in verified business facts. It allows tenants to upload internal reference documents, crawl website pages, catalog structured Q&A pairs, and synchronize live product catalogs from [Google Sheets](./google-sheets-sync.md).

The system converts raw textual context into vector embeddings, storing them inside a PostgreSQL database utilizing the `pgvector` extension. Coupled with [Adaptive RAG](./adaptive-rag.md) and hybrid search algorithms, the knowledge base ensures conversational replies are factual, verified, and strictly protected against hallucinations and injection vulnerabilities.

---

## Technical Architecture

```mermaid
graph TD
    A[Ingestion Sources: PDF / DOCX / URL / Google Sheets] --> B[Parser & Text Sanitizer]
    B --> C[Semantic Chunking Engine]
    C --> D[Embedding Generator (BullMQ Queue)]
    D --> E[(pgvector PostgreSQL Table)]
    F[Customer Inquiry] --> G[Hybrid Search Controller]
    G -->|Dense Cosine Search via Parameterized SQL| E
    G -->|Sparse Lexical Keyword Search| H[(PostgreSQL tsvector Index)]
    E & H -->|Reciprocal Rank Fusion| I[Top Re-Ranked Chunks]
    I --> J[AI Agent Prompt Generator]
```

### Architecture Specifications

1. **Ingestion & Text Sanitization**:
   * Ingests reference materials across multiple file formats (PDF, TXT, DOCX, CSV) and public website URLs.
   * Strips HTML markup, binary artifacts, and formatting noise to retain clean textual content.
2. **Semantic Overlapping Chunking**:
   * Text is partitioned into semantically coherent segments (default 500 characters with a 100-character overlap) to preserve context across boundary splits.
3. **Asynchronous Vector Generation (BullMQ)**:
   * Embedding generation is offloaded to Redis BullMQ worker queues (`embedding.processor.ts`), generating dense vectors using OpenAI `text-embedding-3-small` or regional models.
4. **Parameterized Vector Lookups (SQL Injection Immunity)**:
   * All vector distance calculations (`<=>` cosine distance operator) execute using strictly parameterized Prisma `$executeRaw` queries. Raw string concatenation has been completely eliminated from the retrieval pipeline.
5. **Hybrid Search & Reciprocal Rank Fusion (RRF)**:
   * Combines dense vector similarity searches with PostgreSQL full-text keyword indices (`tsvector`), ensuring exact model numbers, SKUs, and proper nouns are retrieved alongside conceptual matches.

---

## Core Features

*   **Multi-Format Document Upload**: Ingests reference text from files (PDF, CSV, TXT, DOCX) uploaded via the dashboard interface.
*   **Website URL Crawler**: Recursively crawls and extracts text from tenant-specified public website links.
*   **Google Sheets Catalog Ingestion**: Automatically transforms synchronized Google Sheets rows into searchable vector chunks.
*   **Q&A Ingestion Editor**: Allows manual creation and editing of question-and-answer pairs, giving administrators exact control over replies to specific queries.
*   **Chunk Editor & Metadata Inspector**: Provides tools to review, edit, or delete raw text chunks stored in the vector database to correct outdated facts.
*   **Source Citation Mapping**: Links generated replies to the specific source document or URL, allowing agents to see where the AI retrieved its facts.

---

## Benefits

*   **Zero-Fine-Tuning Instant Updates**: Modifying a document or updating a price updates the AI's response knowledge immediately without costly model retraining.
*   **Hallucination Prevention**: Restricts the AI Agent from using external knowledge, ensuring it only responds using verified company facts.
*   **Contextual Sourcing**: Saves troubleshooting time by showing agents the exact file or link citation used by the AI to answer a query.
*   **Hardened Security**: Parameterized queries guarantee absolute resistance against SQL injection vectors.

---

## FAQ

### Q: What is the maximum file upload size?
**A:** The platform supports document uploads up to 10MB per file. Larger files can be chunked or hosted online for the crawler to index.

### Q: How long does it take for a newly uploaded document to become active?
**A:** Vectorization, embedding generation, and indexing are queued via Redis BullMQ and typically complete in under 15 seconds, making new context active immediately.

---

## Related Documents

* [Adaptive RAG Feature](./adaptive-rag.md)
* [Google Sheets Synchronization](./google-sheets-sync.md)
* [Sentinel Security & Parameterized SQL](./sentinel-security.md)
* [AI Agent Product](../products/ai-agent.md)
