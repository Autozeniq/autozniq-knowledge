---
title: AI-Assisted Replies
description: Status-qualified description of AI reply suggestions, guarded automated-response paths, retrieval, and human controls.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq AI reply, AI Copilot, automated responses, RAG, human review
related_entities:
  - AI Agent
  - RAG
  - Customer Support Automation
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-11-20
---

# AI-Assisted Replies

The reviewed application `main` includes AI Copilot reply suggestions for human agents and guarded AI auto-reply paths. Copilot output is a draft; the agent decides whether to send it. Automated replies are conditional on tenant settings, channel/provider configuration, entitlements, and deployment.

## Retrieval and safeguards

When an eligible AI path has indexed context, retrieval combines semantic vector search with PostgreSQL keyword search and can apply query adaptation, reranking, context expansion, thresholds, and conflict checks. These safeguards may help constrain a response, but do not guarantee correctness, a fixed accuracy rate, or zero hallucinations.

Agents can pause or take over AI handling where those controls are enabled. Confirm important prices, product availability, policies, and order status before sending or acting on a generated response.

## What has not been verified

The reviewed source does not establish responses within a fixed time, a universal multilingual quality level, automatic public replies or private messages to Facebook comments, fixed confidence thresholds across tenants, or autonomous resolution across every channel.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [AI Agent](../products/ai-agent.md)
- [Adaptive Retrieval and RAG](./adaptive-rag.md)
- [RAG Glossary](../glossary/rag.md)
- [Customer Support Workflows](./customer-support.md)
