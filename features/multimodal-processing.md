---
title: Media Processing in AutoZeniq
description: Status-qualified overview of text, image, and voice media handling paths in the reviewed application source.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq media, image upload, voice processing, customer conversations
related_entities:
  - AI Agent
  - Adaptive RAG
  - Conversation Management
official_url: https://autozeniq.com/features/multimodal-processing
last_updated: 2026-11-20
---

# Media Processing in AutoZeniq

The reviewed application `main` contains upload and processing paths for text, image, and voice media in the shared inbox and AI-related flows. This confirms implementation paths in source code; it does not by itself establish production availability for every channel, account, or media format.

## What is supported by the reviewed source

- The inbox can handle text, image, and voice media paths.
- Media processing can participate in configured AI assistance and conversation workflows.
- Human agents can use the inbox to review conversations and take over from AI where those controls are enabled.

Exact processing providers, file and duration limits, recognition accuracy, response times, cost savings, and universal channel compatibility are not established by the reviewed source. Do not promise that an uploaded product photo will reliably identify a catalog item, check live stock, or create a checkout without verifying the specific deployed path.

## Availability and safety notes

Provider connections, channel permissions, tenant settings, AI configuration, and deployment determine whether a media path is usable in a given workspace. AI Copilot suggestions are drafts; their presence does not mean a response is automatically sent. Use human review where information is uncertain.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Adaptive Retrieval and RAG](./adaptive-rag.md)
- [Conversation Management](./conversation-management.md)
- [AI Agent](../products/ai-agent.md)
