---
title: Customer Support Workflows
description: Verified inbox, AI assistance, knowledge retrieval, and human handover paths with current limitations.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq customer support, shared inbox, AI assistance, knowledge retrieval, human takeover
related_entities:
  - AI Agent
  - Customer Support Automation
  - Adaptive RAG
official_url: https://autozeniq.com/solutions/customer-support
last_updated: 2026-11-20
---

# Customer Support Workflows

The reviewed application `main` contains a tenant-scoped shared inbox for conversation search and listing, message history, human replies, assignment, AI pause/takeover/resume, and selected real-time updates. Configured AI paths can use indexed knowledge context, and AI Copilot suggestions are drafts for an agent to review.

## Knowledge and AI assistance

Supported document and data sources can be parsed and indexed asynchronously. Conversational retrieval combines semantic vector search with PostgreSQL keyword search and can apply query adaptation, reranking, context expansion, thresholds, and conflict checks. These mechanisms can help constrain replies, but they do not guarantee correctness or eliminate hallucinations.

Guarded AI auto-reply paths exist in the reviewed code, but availability depends on AI settings, channel/provider configuration, entitlements, and deployment. A draft suggestion is not automatically sent. Verify important prices, policies, stock, and order information before replying.

## Human handling

Agents can use inbox controls to reply, assign conversations, and pause or take over AI handling where supported. The reviewed source does not establish a complete ticketing system, internal team notes, universal round-robin assignment, user-visible confidence thresholds, URL crawling, or automatic escalation for every unsupported answer.

## Availability notes

A channel adapter or OAuth path in source is not proof that a provider account is approved or connected. Real-time behavior is limited to selected updates; do not claim universal typing indicators, read receipts, presence, or collision locks.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Knowledge Base](./knowledge-base.md)
- [Conversation Management](./conversation-management.md)
- [AI Agent](../products/ai-agent.md)
- [Adaptive Retrieval and RAG](./adaptive-rag.md)
