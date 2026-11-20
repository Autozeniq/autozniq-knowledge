---
title: AutoZeniq Knowledge Base and Retrieval
description: Merchant guide to adding business information for configured AI assistance.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq knowledge base, business information, AI assistance, retrieval
related_entities:
  - Adaptive RAG
  - Google Sheets Synchronization
  - AI Assistance
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-11-20
---
# Knowledge Base and Retrieval

**Status: Partially Available.** The Knowledge Base can help configured AI assistance use selected business information when preparing replies. It is intended for merchants and support teams that want drafts to reflect their current shop information. Adding sources and processing them requires configuration; available sources and live synchronization depend on workspace and account setup.

## Setup and basic workflow

A team member with permission to manage sources adds or connects supported business information and checks the processing status shown in the workspace. Confirm that the workspace has access to an eligible AI feature, then test a representative question in a conversation and review the result before depending on it. A person remains responsible for the final reply. The exact source types, size limits, and setup steps depend on what the workspace currently supports.

**Configuration Required:** The user needs permission to manage sources, sources must be readable and supported, and the workspace must have eligible AI access. Processing may take time. A processing indicator does not guarantee that every AI response will use or accurately reflect a source.

## Retrieval, limits, and troubleshooting

**Status: Partially Available.** Configured retrieval may bring relevant source information into an AI draft, but it does not guarantee a correct answer, citations, a fixed processing time, or zero mistakes. Review prices, policies, inventory, and support instructions before sending an AI-generated reply.

**Needs Verification:** Website crawling, a full question-and-answer editor, and knowledge-gap reporting should be confirmed in the workspace before being promised. Google Sheets import is a separate, partially available integration; see [Google Sheets Synchronization](./google-sheets-sync.md). A connected or previewed source does not by itself prove that it is fully synchronized or being used by AI.

If a source is not used, check its access, readability, processing status, and whether AI assistance is configured to use the workspace knowledge base. Replace unreadable or outdated information and retry only when the workspace indicates it is safe. If the issue remains, use the current support route with the source name and displayed processing error; do not share credentials.

## Related features

[AI Assistance](../products/ai-agent.md) explains how a human reviews AI drafts; [Adaptive Retrieval](./adaptive-rag.md) describes related retrieval guidance; [Google Sheets Synchronization](./google-sheets-sync.md) covers that separate integration. These related pages do not establish source availability or live synchronization for a particular workspace.
