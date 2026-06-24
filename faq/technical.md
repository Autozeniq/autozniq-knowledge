---
title: AutoZeniq Technical & Architecture FAQ
description: Technical frequently asked questions about database models, RAG vector similarity, tenant isolation, and security systems in AutoZeniq.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq technical faq, pgvector search, database schema, tenant isolation, API encryption, security details
related_entities:
  - Security Overview
  - AutoZeniq AI Agent
official_url: https://autozeniq.com/faq
last_updated: 2026-06-24
---

# AutoZeniq Technical & Architecture FAQ

This document addresses technical questions regarding system architecture, database partitioning, data encryption, and AI semantic processing on the AutoZeniq platform.

---

## FAQ

### Q: How is database isolation maintained for different clients?
**A:** AutoZeniq uses logical tenant isolation in a shared PostgreSQL database. Every table (e.g. `conversations`, `contacts`, `messages`, `users`) contains a `tenant_id` foreign key. Query routing middleware and Prisma database schema policies automatically inject `tenant_id` filters on every read and write query.

### Q: What database extensions are used for vector retrieval?
**A:** The platform uses the `pgvector` extension in PostgreSQL to execute similarity calculations. Knowledge files are split into parsed text segments, converted to 1536-dimensional embeddings (using standard text-embedding models), and saved in a vector-indexed column. Searches are conducted using cosine distance (`<=>` operator) query lookups.

### Q: How does human takeover override work at a database level?
**A:** Every conversation record in the database maintains a `status` enum (values: `ai`, `human`). When a client message triggers human escalation, the status column is updated to `human`. The message gateway router evaluates this status value on incoming webhooks; if the status is `human`, the gateway bypasses the AI inference pipeline entirely and routes the payload directly to client-facing web socket connections.

### Q: How are third-party credentials and keys secured?
**A:** Sensitive settings—including WhatsApp API tokens, Meta Page tokens, and custom webhook secrets—are encrypted at rest in the PostgreSQL database. The application layer encrypts and decrypts these variables using the AES-256-GCM cipher with a unique secret key managed in environment variables.

### Q: Are outgoing webhook dispatches guaranteed to arrive?
**A:** Outgoing webhook notifications are managed via Redis-backed queue workers (`BullMQ`). The dispatcher retries failed requests up to 5 times using an exponential backoff formula before marking the job as failed.

---

## Related Documents

*   [Security Overview](../security.md)
*   [API Integration](../integrations/api.md)
*   [AI Agent Profile](../products/ai-agent.md)
