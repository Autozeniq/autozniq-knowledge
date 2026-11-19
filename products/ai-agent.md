---
title: AutoZeniq AI Assistance
description: Reviewed AI assistance, retrieval, configuration, and human-review paths, with availability and automation limits.
keywords: AutoZeniq AI, AI Copilot, Adaptive RAG, reply suggestions, human takeover
category: product
entity: AutoZeniq
type: Product
related_entities:
  - Customer Support Automation
  - Commerce Automation
  - Adaptive RAG
  - Media Processing
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-11-20
---

# AutoZeniq AI Assistance

The reviewed application `main` contains AI-assisted customer support paths, tenant AI settings and rules, knowledge retrieval, and human controls. The AI Copilot can prepare reply suggestions for an agent. These suggestions are drafts, not automatically sent messages.

Other guarded AI auto-reply paths are present in the code, but their use depends on tenant configuration, channel/provider setup, entitlements, and deployment. The existence of these paths is not a promise that every conversation receives an automatic AI response or that AI can independently complete an order.

## Knowledge retrieval and media

Conversational retrieval combines semantic vector search with PostgreSQL keyword search and can apply query adaptation, reranking, context expansion, thresholds, and conflict checks. The inbox has text, image, and voice media upload/processing paths. See [Adaptive Retrieval and RAG](../features/adaptive-rag.md) and [Media Processing](../features/multimodal-processing.md) for scope and limits.

## Human review and limitations

Agents can pause, take over, and resume AI handling where configured. Retrieved context and guardrails can help constrain responses, but they do not eliminate hallucinations or guarantee factual correctness. No fixed accuracy, latency, cost-savings, conversion, or support-deflection figure is established by the reviewed source. Verify important policies, prices, stock, and order details before acting on an AI response.

## Availability

Model/provider configuration, tenant AI settings, channel connection, entitlements, and deployment affect availability. A connector or model mapping in source code does not prove an account is approved or operational in production.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Adaptive Retrieval and RAG](../features/adaptive-rag.md)
- [Media Processing](../features/multimodal-processing.md)
- [Order Management](./order-management.md)
- [Conversation Management](../features/conversation-management.md)
