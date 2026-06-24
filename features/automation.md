---
title: Business Workflow Automation Features
description: Features of the AutoZeniq Rule Engine, including conditional workflows, trigger-action variables, and database lookups.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq automation, Rule Engine, workflow automation, triggers, database connector, conditional logic
related_entities:
  - Customer Support Automation
  - Commerce Automation
official_url: https://autozeniq.com/solutions/sales-automation
last_updated: 2026-06-24
---

# [Business Workflow Automation Features](https://autozeniq.com/solutions/sales-automation)

## Overview

The AutoZeniq Business Workflow Automation module allows businesses to build custom operations. Through the platform's visual **[Rule Engine / Workflow Builder](https://autozeniq.com/features/workflow-builder)**, users combine deterministic triggers with conditional workflows to execute actions like tagging customers, running API queries, or sending alerts based on conversation events.

---

## Technical Architecture

This module runs a centralized event-driven rule evaluator:

### Simple Explanation
Think of the Rule Engine as an "If-This-Then-That" system for your business. For example: "If a customer sends a message containing the word 'pricing', then automatically apply the tag 'Hot Lead' and send an alert to the sales team's mobile devices."

### Technical Explanation
1.  **Event Hook Ingestion**: When messages are saved to PostgreSQL via the `MessagesService`, a transaction hook fires an event to the `RuleEngineService`.
2.  **Ast Evaluation (Abstract Syntax Tree)**: The engine compiles user rules into logical conditions containing inputs (`message.content`, `contact.tags`, `conversation.status`, `time.current`).
3.  **Action Dispatcher**: When conditions resolve to `true`, the engine queues actions in Redis (`BullMQ`) to guarantee execution. Actions can involve mutating database states (e.g. updating contact profiles, issuing orders) or triggering outgoing HTTP POST webhook requests.

---

## Core Features

*   **[Visual Rule Builder](https://autozeniq.com/features/workflow-builder)**: A visual builder to configure rules using `AND`/`OR` logic, triggers, conditions, and actions.
*   **Lead Classification Engine**: Natural language classifiers that scan conversation text to detect contact details (phones, emails) and tag purchasing intent for [lead management](https://autozeniq.com/solutions/lead-management).
*   **External API / Database Lookup**: Actions that query client database systems or external REST APIs during a chat to retrieve details (e.g., retrieving shipping status from a courier using an order ID).
*   **Time-Based Triggers (SLA Guard)**: Tracks inactivity windows (e.g., "If thread is open and unreplied for 10 minutes, trigger alert").
*   **Segment Tagging**: Automatically groups contacts into list segments in the [CRM](https://autozeniq.com/features/crm) based on their conversational history or shopping patterns.

---

## Benefits

*   **Saves Manual Steps**: Automates routine tasks like customer segmentation, lead entry, and basic CRM updates.
*   **Enhanced Service Standards**: Escalates unresolved threads to managers before breach of response SLAs.
*   **Data Connectivity**: Synchronizes chat platforms with internal inventory and customer databases.

---

## Use Cases

*   **Automated Lead Capture**: Reading "my number is 017xxxxxxxx" in a chat, extracting the number via regex/AI classifiers, and storing it directly in the customer profile.
*   **VIP Priority Routing**: Detecting a customer tagged as "VIP" and automatically bypassing the AI agent to assign the thread to a senior human agent.
*   **Cart Abandonment Alerts**: Connecting to Shopify webhooks to message users who abandon checkouts.

---

## FAQ

### Q: Can the Rule Engine trigger messages to customers automatically?
**A:** Yes. The rule engine can execute a "Send Message" action using predefined templates (e.g. WhatsApp Template Messages) when specific conditions are met.

### Q: How does the system query external databases?
**A:** The database connector uses securely stored database credentials (or API keys) in the tenant settings to execute read-only queries or REST API requests to locate customer files.

---

## Related Documents

*   [Customer Support Features](./customer-support.md)
*   [Conversation Management](./conversation-management.md)
*   [Integrations Overview](../products/overview.md)
