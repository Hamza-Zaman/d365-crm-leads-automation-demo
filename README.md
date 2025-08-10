# Dynamics 365 CRM Demo — Lead Tracking, Segmentation, and Marketing Automation

This repository shows how I would customise **Microsoft Dynamics 365** (Dataverse) to support:
- Lead capture with UTM parameters and consent
- Lead scoring and auto-assignment
- Customer segmentation (rules-based) for B2B/B2C
- Real-time marketing journeys and reporting in Power BI

> Status: Initial scaffold created on 2025-08-10 with realistic examples and placeholders you can adapt to your tenant.

## Repository structure
- **/flows** — Example **Power Automate** flows (HTTP ingest, lead scoring update)
- **/api** — **Dataverse Web API** examples for create/update/query
- **/segments** — Segmentation rules for Customer Insights – Journeys
- **/powerbi** — Star schema notes and DAX ideas for CRM KPIs
- **/docs** — Customisation guide (entities, fields, forms, views, security)

## How this fits together
1. Web form or ad platform sends a lead (HTTP) → Power Automate → **Dataverse Lead**
2. Flow updates `LeadScore`, sets owner or queue, and logs interactions
3. Customer Insights – Journeys uses rules to segment contacts/leads
4. Journeys trigger emails/SMS and create follow-up tasks for sellers
5. **Power BI** reports MQL/SQL conversion, cycle time, and campaign ROI

## What to adjust before running
- Replace placeholders such as **{org}**, **{token}**, and custom field prefixes (e.g., `hmz_`) with your tenant values.
- Import the JSON flows into **Power Automate** and map to your tables and fields.
- Use the `.http` API file with VS Code REST Client or Postman for quick tests.
