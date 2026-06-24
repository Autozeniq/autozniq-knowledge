---
title: AutoZeniq Analyst Agent
description: Technical specifications, aggregate queries, log parsing, and metric compilation details for the AutoZeniq Analyst sub-agent.
entity: AutoZeniq
type: Agent
category: product
keywords: AutoZeniq Analyst Agent, Analyst Agent, analytics agent, dashboard metrics, customer logs
related_entities:
  - AutoZeniq AI Agent
  - Terminology
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-06-24
---

# AutoZeniq Analyst Agent

The **AutoZeniq Analyst Agent** is a data-oriented sub-agent of the AutoZeniq AI Agent system. It compiles customer interaction logs, evaluates conversion rates, calculates support resolution metrics, and generates analytical reports for the business dashboard.

---

## User Explanation

The Analyst Agent acts as a business reporter. It reviews all chat histories, orders, and customer feedbacks to find important trends. It answers questions like: "What was our busiest hour yesterday?", "How many leads did we capture this week?", or "What are customers complaining about the most?". This helps business owners understand how their sales and support teams (and the AI itself) are performing.

---

## Technical Specifications

The Analyst Agent operates on read-only transaction and interaction logs:

*   **Database Query Scope**: Executes read-only queries against tables such as `conversations`, `messages`, `contacts`, and `orders`. All database operations are restricted using parameterized SQL containing `WHERE tenant_id = :tenant_id` guards.
*   **Metric Calculations**: Computes key performance indicators (KPIs) including:
    *   *AI Auto-Resolution Rate*: Percentage of customer threads resolved by the AI without manual human agent takeover.
    *   *Average Response Time*: The delay duration between incoming customer webhooks and outbound replies.
    *   *Lead Conversion Rate*: Ratio of qualified leads (with contact information) to overall conversation threads.
*   **Interaction Log Clustering**: Uses natural language processing models to group message contents into semantic clusters, highlighting top complaint topics or popular products.
*   **Serialization**: Formats data responses into clean JSON datasets for dashboard rendering components or Markdown tables for admin summary emails.

---

## Use Cases

*   **Weekly Conversions Reports**: Summarizing the total count of captured leads and generated checkout invoices.
*   **Common Complaint Identification**: Highlighting which keywords or product questions trigger the highest rate of manual agent escalations.
*   **Performance Monitoring**: Monitoring hourly and daily chat volumes to adjust staff schedules.

---

## Related Documents

*   [AutoZeniq AI Agent](../ai-agent.md)
*   [Terminology](../../brand/terminology.md)
*   [Security Overview](../../security.md)
