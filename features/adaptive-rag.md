---
title: AutoZeniq Adaptive Retrieval and RAG
description: Merchant-facing overview of knowledge retrieval, response context, availability, and limits.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq RAG, hybrid search, query rewriting, retrieval
related_entities:
  - RAG
  - AI Agent
  - Knowledge Base Feature
official_url: https://autozeniq.com/features/adaptive-rag
last_updated: 2026-11-20
---
# Adaptive Retrieval and RAG

**Status: Partially Available.** When a workspace has successfully processed knowledge sources and an eligible AI feature is enabled, AutoZeniq can retrieve relevant information to help prepare a response. Retrieval may combine meaning-based and keyword matching, adapt a question, rank results, and check for conflicting sources.

## Prerequisites

- A workspace role that can manage knowledge and AI settings.
- At least one supported source added and successfully processed.
- An enabled AI feature, supported channel, provider connection, and available entitlement.
- Current product, policy, and pricing information in the connected sources.

## Limits

Retrieval can reduce unsupported answers but does not guarantee correctness, citations, zero hallucinations, a fixed confidence score, provider failover, or a fixed response time. It does not guarantee that a recent product or spreadsheet change is immediately available to the AI.

AI Copilot output is a draft for review. Confirm prices, stock, policies, and order details before sending or acting on a response.

## Troubleshooting

If responses do not use a source, confirm that processing finished successfully, the source is readable and current, the AI feature is enabled, and the conversation is on a supported channel. Reprocess or replace incomplete sources and retry. See [Knowledge Base](./knowledge-base.md) and [AI Assistance](../products/ai-agent.md).

## Related documents

- [Knowledge Base](./knowledge-base.md)
- [AI Assistance](../products/ai-agent.md)
- [Google Sheets Synchronization](./google-sheets-sync.md)
