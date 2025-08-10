# Customisation Guide (Dynamics 365 / Dataverse)

## Entities and fields
**Lead** (custom fields, example prefix `hmz_`):
- `hmz_utm_source` (Text)
- `hmz_utm_medium` (Text)
- `hmz_utm_campaign` (Text)
- `hmz_consentstatus` (Two Options)
- `hmz_leadscore` (Whole Number)
- `hmz_segmenttag` (Text)

**Contact** (custom fields):
- `hmz_persona` (Choice)
- `hmz_industry` (Choice)
- `hmz_lastinteraction` (DateTime)

**Campaign** (custom fields):
- `hmz_channelmix` (Choice)
- `hmz_budget` (Currency)

## Forms and views
- Lead main form: add UTM + Consent + LeadScore section; include a Timeline for interactions
- Views: "New Leads (Last 7 Days)", "MQLs by Source", "Leads Requiring Follow-up" (LeadScore >= threshold)

## Business rules and processes
- Enforce consent capture for email/SMS
- Auto-calculate LeadScore from recent interactions (opened/clicked emails, pages viewed, form submits)
- Assignment rules by territory or product interest (owner/team)

## Power Automate flows
- **Lead Ingest (HTTP)**: Accepts JSON payload from web form, creates/updates Lead with UTM fields and Consent
- **Lead Score Update**: Daily job or Dataverse-triggered, recalculates `hmz_leadscore`, creates tasks if threshold met
- **Notify Seller**: Teams/Email notification when high-intent lead is created

## Segmentation (Customer Insights – Journeys)
- High Intent: LeadScore >= 70 AND utm_medium = "cpc"
- Warm: LeadScore 40–69 AND consent = True
- Dormant: No interaction in last 90 days
- Manufacturing: Industry in {"Manufacturing","Construction","Utilities"}

## Power BI reporting
- Star schema: FactLeads + DimDate + DimSource + DimCampaign + DimOwner
- KPIs: MQL→SQL conversion %, cycle time, campaign ROI, cost per SQL
- Slicers: UTM parameters, segments, owner/team

## Security and compliance
- Security roles to restrict export
- Audit for consent changes
- DLP policies for connectors
