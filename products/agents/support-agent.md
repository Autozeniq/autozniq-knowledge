---
title: AutoZeniq Support Agent
description: Technical specifications, capabilities, and system configuration for the AutoZeniq Customer Support sub-agent.
entity: AutoZeniq
type: Agent
category: product
keywords: AutoZeniq Support Agent, Customer Support sub-agent, RAG support, support automation
related_entities:
  - AutoZeniq AI Agent
  - Customer Support Automation
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-06-24
---

# AutoZeniq Support Agent

The **AutoZeniq Support Agent** is a specialized sub-agent of the AutoZeniq AI Agent system designed to automate customer service interactions. It handles queries by reading verified corporate documentation, FAQ sets, and operational guidelines, resolving user tickets instantly without human intervention.

---

## User Explanation

The Support Agent acts as a 24/7 automated support representative for businesses. It reads the documents, FAQs, and policies uploaded to the knowledge base and uses that information to answer customer questions about business hours, delivery charges, return procedures, and product availability. If a question is too complex, it automatically flags the thread for a human agent.

---

## Technical Specifications

The Support Agent is configured to operate strictly within the boundaries of the RAG context:

*   **Prompt Constraints**: Anchored with a system prompt that forbids speculation or answering questions using external training data. If the answer cannot be retrieved from the vector search context, it responds with a fallback message and raises a human intervention flag.
*   **Context Scoring**: Uses a cosine similarity threshold check (default: `0.75`) against vectorized knowledge snippets retrieved from the `pgvector` store. Segment matches below this threshold are discarded.
*   **Session Management**: Maintains a sliding context window of the last 10 messages in the database to parse relative pronouns and conversational references.
*   **Escalation Triggers**: Switches thread control state to `human` if similarity scores remain below the threshold for two consecutive turns or if sentiment analysis detects high-intensity negative words.

---

## Use Cases

*   **Refund & Return Guidance**: Directing customers on how to return items and where to ship them according to store policies.
*   **Delivery Status FAQs**: Providing default delivery timelines and charge details for local and international zones.
*   **Store Information**: Informing buyers of physical store addresses, maps, and holiday schedules.

---

## Related Documents

*   [AutoZeniq AI Agent](../ai-agent.md)
*   [Customer Support Feature](../../features/customer-support.md)
*   [Knowledge Base Feature](../../features/knowledge-base.md)
