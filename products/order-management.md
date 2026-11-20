---
title: AutoZeniq Order Management System
description: Merchant guide to order review, inventory, payment records, delivery handoff, and returns.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq orders, order status, inventory, payment modes, checkout
related_entities:
  - Storefront Builder
  - Delivery Logistics
  - Returns and Exchanges
  - Billing and Entitlements
official_url: https://autozeniq.com/products/order-management
last_updated: 2026-11-20
---
# AutoZeniq Order Management System

**Status: Partially Available.** Orders and payments helps merchants review customer orders, configured payment records, stock changes, delivery handoff, and return requests in a connected workflow. It is intended for shop owners and team members who manage online orders and customer support. The available actions and order statuses vary by workspace and connected services.

## How the workflow works

Review the order and its customer, item, and payment details. Where enabled, check configured payment modes, payment links, and staged balances. Confirm stock and delivery details before handoff, then review the order and provider records as the order progresses. An order can move through configured creation, confirmation, processing, courier, delivery, return, or exchange stages; exact status names and automatic updates need confirmation for the workspace. A displayed order status is not proof of payment.

## Setup and prerequisites

Before relying on the workflow, confirm workspace access and plan availability, catalog and inventory settings, currency and payment-provider configuration, and the selected courier account and permissions. Payment links and staged balances are available only where enabled. Live availability depends on workspace enablement and connected services.

Configured workflows can reserve, deduct, release, adjust, or restock inventory. Review the resulting stock and order record after cancellation, return, or exchange; do not assume every status change automatically restocks. Courier booking and tracking require the selected courier connection and account authorization. See [Delivery and Logistics](./delivery-logistics.md).

## Payment evidence

**Status: Partially Available.** Payment status should be based on verified online-provider evidence or another independently verified payment record. COD collection instructions tell a courier what to collect; they do not prove the customer paid. Courier delivery, remittance, settlement, or balance information must not automatically mark an order `PAID`. For an unclear result, preserve the order record and check the workspace’s available reconciliation process before retrying.

## Returns and exchanges

**Status: Configuration Required.** Merchants may manage eligible return or exchange requests in the configured workflow. Approval, restocking, replacement stock, reverse pickup, and refunds are separate actions. A return record or courier event is not proof that a refund was issued.

## Errors and related features

For duplicate submissions, rejected addresses, stock conflicts, provider failures, or ambiguous payment or delivery results, keep the order record, review the visible error, and avoid blind retries that could create a duplicate order or booking.

The storefront can create customer orders; [Billing and Entitlements](../features/billing-entitlements.md) explains workspace plan and payment setup; [Delivery and Logistics](./delivery-logistics.md) covers courier handoff; [Returns and Exchanges](../features/returns-takeover-automation.md) covers merchant-mediated return handling. These related areas have their own setup and availability limits.
