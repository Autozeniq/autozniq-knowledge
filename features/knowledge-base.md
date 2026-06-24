---
title: Knowledge Base Feature
description: Detailed features of the AutoZeniq RAG Knowledge Base, document parsing, website crawling, and pgvector database indexing.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq knowledge base, RAG, document ingestion, vector database, pgvector, crawler, text chunking
related_entities:
  - RAG
  - Terminology
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-06-24
---

# Knowledge Base Feature

## Overview

The AutoZeniq **Knowledge Base** is the data-ingestion workspace. It allows tenants to upload reference documents, import website links, and catalog Q&A datasets. The system converts this data into vector embeddings, saving them in a PostgreSQL database using the `pgvector` extension. This provides the semantic context that guides the AI Agent's automated responses.

---

## Technical Architecture

The knowledge base manages a document vectorization and indexing pipeline:

### Simple Explanation
Think of the Knowledge Base as a digital library built specifically for your business. You upload your product catalogs, return policies, or store directories, or type in your website link. AutoZeniq's system reads these files, breaks the information down into searchable chunks, and stores them securely. When a customer asks a question, the AI Agent quickly searches this library to retrieve the correct facts.

### Technical Explanation
1.  **Ingestion & Text Extraction**: Tenants upload files (PDF, TXT, DOCX, CSV) or input website URLs. The system parses the raw data to extract clean text, filtering out HTML tags, styling elements, and binary formatting.
2.  **Semantic Chunking**: The extracted text is split into smaller, overlapping segments (chunks). By default, the chunk size is configured to 500 characters with an overlap of 100 characters to preserve context across boundaries.
3.  **Vector Generation**: Each text chunk is sent to an embedding model (e.g. OpenAI's `text-embedding-3-small` or HuggingFace alternatives) to generate a high-dimensional vector.
4.  **Database Storage (`pgvector`)**: The vector coordinates, raw text content, source file metadata, and `tenant_id` are saved in the PostgreSQL `knowledge_base_chunks` table. A Hierarchical Navigable Small World (HNSW) index is created on the vector column to speed up semantic lookup queries.

---

## Core Features

*   **Multi-Format Document Upload**: Ingests reference text from files (PDF, CSV, TXT, DOCX) uploaded via the dashboard interface.
*   **Website URL Crawler**: Recursively crawls and extracts text from tenant-specified public website links.
*   **Q&A Ingestion Editor**: Allows manual creation and editing of question-and-answer pairs, giving administrators exact control over replies to specific queries.
*   **Chunk Editor Dashboard**: Provides tools to review, edit, or delete raw text chunks stored in the vector database to correct outdated facts.
*   **Source Citation Mapping**: Links generated replies to the specific source document or URL, allowing agents to see where the AI retrieved its facts.

---

## Benefits

*   **Fast Context Updates**: Eliminates the need for expensive model fine-tuning; modifying a document updates the AI's response parameters immediately.
*   **Hallucination Prevention**: Restricts the AI Agent from using external knowledge, ensuring it only responds using verified company facts.
*   **Contextual Sourcing**: Saves troubleshooting time by showing agents the exact file or link citation used by the AI to answer a query.

---

## FAQ

### Q: What is the maximum file upload size?
**A:** The platform supports document uploads up to 10MB per file. Larger files should be split or hosted online for the crawler to index.

### Q: How long does it take for a newly uploaded document to become active?
**A:** Vectorization, embedding generation, and indexing are queued via Redis (`BullMQ`) and are typically completed in under 30 seconds, making the new context active immediately.

---

## Related Documents

*   [Customer Support Features](./customer-support.md)
*   [RAG Glossary Definition](../glossary/rag.md)
*   [AI Agent Product](../products/ai-agent.md)
