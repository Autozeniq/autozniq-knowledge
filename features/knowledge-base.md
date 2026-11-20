---
title: AutoZeniq Knowledge Base and Retrieval
description: Guide to supported knowledge sources, processing, retrieval, prerequisites, and boundaries.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq knowledge base, RAG, document ingestion, retrieval
related_entities:
  - RAG
  - Adaptive RAG
  - Google Sheets Synchronization
  - AI Agent
official_url: https://autozeniq.com/features/knowledge-base
last_updated: 2026-11-20
---
# Knowledge Base and Retrieval

**Status: Configuration Required.** Eligible workspaces can add supported PDF, DOC/DOCX, CSV, JSON, and plain-text files for processing and use in configured AI assistance. Processing is asynchronous; a source must finish successfully before it can be used reliably.

## Retrieval features

**Status: Partially Available.** Retrieval may match meaning and keywords, adapt a question, rank relevant content, include surrounding context, and flag possible conflicts. These safeguards help an AI response use workspace information but do not guarantee correctness, citations, fixed indexing time, or zero hallucinations.

## Prerequisites and boundaries

- The user needs permission to manage knowledge sources.
- Files must be readable and within the currently supported size and format limits.
- The workspace must have an eligible AI feature and entitlement.
- Google Sheets import is a separate, partially available integration; see [Google Sheets Synchronization](./google-sheets-sync.md).
- **Needs Verification:** Website crawling, a full question-and-answer editor, and knowledge-gap reporting should be confirmed in the workspace before being promised.

Keep prices, policies, inventory, and support instructions current. AI Copilot output remains a draft for human review.

## Troubleshooting

If a source is not used, check its format, access, processing status, and whether the AI feature is connected to the workspace knowledge base. Replace unreadable or outdated files and retry processing. If results remain incomplete, provide the source name and processing error to support.

## Related documents

- [Adaptive RAG](./adaptive-rag.md)
- [Google Sheets Synchronization](./google-sheets-sync.md)
- [AI Assistance](../products/ai-agent.md)
