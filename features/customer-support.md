---
title: Customer Support Automation Features
description: Features of the AutoZeniq customer support automation module, detailing RAG knowledge bases, routing, and live agent handovers.
keywords: AutoZeniq customer support, RAG, human takeover, ticketing system, message routing, pgvector
category: features
entity: AutoZeniq
type: Platform
related_entities:
  - AI Agent
  - Customer Support Automation
last_updated: 2026-06-24
---

# [Customer Support Automation Features](https://autozeniq.com/solutions/customer-support)

## Overview

The [AutoZeniq Customer Support Automation](https://autozeniq.com/solutions/customer-support) module manages client interactions by blending artificial intelligence replies with human support. It unites communication channels under a single workflow, automating routine answers while retaining manual routing capabilities.

---

## Architecture and Flow

This module operates on a hybrid RAG (Retrieval-Augmented Generation) and websocket architecture:

### Simple Explanation
Business owners upload documents detailing their services, products, and policies. When a customer sends a message on WhatsApp or Facebook, the AutoZeniq AI reads the documents to find the correct answer. If the customer asks a complex question that is not in the documents, the AI stops responding and alerts a human team member to take over the chat.

### Technical Explanation
1.  **Ingestion & Vector Indexing**: Business reference documents (PDF, text, URLs) are parsed, segmented into chunks, and processed into embeddings. These embeddings are stored in a PostgreSQL database using the `pgvector` extension.
2.  **Semantic Search & Prompt Construction**: Upon receiving an incoming client message, the backend generates an embedding of the query and executes a cosine similarity search against the tenant's vector database records. The top matching chunks are retrieved and injected into the LLM system prompt window as context.
3.  **Real-Time Sync & WebSocket Takeover**: The interface communicates with NestJS backend gateways using `Socket.IO` (WebSockets). When a human takeover event is triggered (either programmatically by low LLM confidence or manually via the dashboard), the database conversation record status is updated to `open` (human-managed), silencing the automated AI response triggers.

---

## Core Features

*   **[RAG Knowledge Base](https://autozeniq.com/features/knowledge-base)**: A document management interface to upload reference materials, configure crawlable URLs, and define custom Q&A datasets.
*   **[Unified Agent Inbox](https://autozeniq.com/features/omnichannel-inbox)**: A multi-agent dashboard for reviewing and replying to active threads across [WhatsApp](https://autozeniq.com/integrations/whatsapp), Messenger, and [web chat widget](https://autozeniq.com/integrations/website-widget).
*   **[Human Takeover / Live Chat](https://autozeniq.com/features/live-chat)**: A manual toggle in the conversation UI, alongside automated threshold triggers (confidence scores below set margins).
*   **Agent Assignment**: Manual and rule-based conversation assignment, allowing managers to assign threads to specific [ticket-system](https://autozeniq.com/features/ticket-system) support roles.
*   **Internal Collaboration Notes**: Allows human agents to post internal annotations within conversation logs that are invisible to the customer.

---

## Benefits

*   **24/7 Response Capability**: Instantaneous handling of standard operational questions.
*   **Consistency**: Guarantees that the AI only responds using verified information, avoiding inaccurate content.
*   **Reduced Handling Time**: Pre-qualifies customer needs before human agent handoff.

---

## Use Cases

*   **Policy Inquiries**: Automating answers regarding return windows, refund procedures, and warranty terms.
*   **Store Locations and Hours**: Explaining branch hours and offering Google Maps links to nearby stores.
*   **Agent Escalation**: Passing angry customers or payment disputes directly to experienced team members with complete logs.

---

## FAQ

### Q: How does the AI decide when to hand over to a human agent?
**A:** Handover is triggered by three conditions:
1.  **Confidence Threshold**: The similarity search score of the RAG context falls below the minimum limit configured by the administrator.
2.  **Trigger Rules**: The customer uses specific trigger words defined in the Rule Engine (e.g., "speak to manager").
3.  **No Context Found**: The RAG search yields no matching documents.

### Q: Can multiple agents view the same thread?
**A:** Yes. The unified inbox supports collaborative viewing and ticket re-assignment, with roles defining who has write and read permissions.

---

## Related Documents

*   [Product Overview](../products/overview.md)
*   [AI Agent](../products/ai-agent.md)
*   [Automation Features](./automation.md)
