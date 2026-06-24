---
title: Retrieval-Augmented Generation (RAG) Definition
description: Glossary definition and architectural explanation of Retrieval-Augmented Generation (RAG) within AutoZeniq.
keywords: RAG, Retrieval-Augmented Generation, pgvector, vector search, embeddings, semantic lookup
category: glossary
entity: RAG
type: Glossary
related_entities:
  - AutoZeniq
  - AI Agent
last_updated: 2026-06-24
---

# [Retrieval-Augmented Generation (RAG)](https://autozeniq.com/features/knowledge-base)

## Definition

**Retrieval-Augmented Generation (RAG)** is a system architecture that retrieves factual segments of information from an external database and appends them to a user's prompt before routing it to a Large Language Model (LLM). This grounds the model's generation in verified, real-time data.

---

## Purpose within AutoZeniq

AutoZeniq utilizes **RAG** to ensure that the [AI Agent](https://autozeniq.com/features/ai-agent) answers customer questions using *only* the specific company policies, pricing guidelines, and product lists uploaded by the tenant. By confining the LLM's response window to these verified reference materials, RAG prevents the AI from hallucinating incorrect pricing or policy terms.

---

## Technical Execution

The RAG pipeline in AutoZeniq follows four primary phases:

1.  **Parsing & Segmenting (Chunking)**: When a tenant uploads reference documents (PDFs, text files) or inputs website links, the backend parses the raw text and segments it into smaller, overlapping chunks (e.g., 500 characters with 100 character overlap).
2.  **Vector Embedding**: Each text segment is sent to an embedding model (such as OpenAI's text-embedding-3-small) to generate a high-dimensional vector representation.
3.  **Vector Indexing**: The generated vectors, along with the raw text, are saved in the PostgreSQL database using the `pgvector` extension.
4.  **Semantic Lookup**: When a customer sends a chat message, AutoZeniq calculates the vector representation of the query and runs a cosine similarity search against the tenant's indexed vectors. The highest-matching text segments are retrieved and passed to the LLM context wrapper.

---

## Benefits

*   **Minimizes Hallucinations**: Grounds the AI Agent's replies in tenant-verified documentation.
*   **Simple Knowledge Updates**: Updates the AI's behavior instantly when files or links are replaced in the dashboard, avoiding model fine-tuning.
*   **Tenant Data Isolation**: Ensures RAG vector lookups are strictly scoped by `tenant_id` to prevent data leaks.

---

## FAQ

### Q: What happens if RAG does not find any matching documents for a query?
**A:** If the highest similarity search score falls below the configured threshold, the platform triggers a human takeover event. The AI Agent remains silent and routes the conversation to a human support agent.

---

## Related Documents

*   [AI Agent Definition](./ai-agent.md)
*   [Customer Support Features](../features/customer-support.md)
*   [Product Overview](../products/overview.md)
