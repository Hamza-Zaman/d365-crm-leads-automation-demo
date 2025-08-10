# Power BI Model Notes (CRM)

## Star schema
- FactLeads (leadid, createdon, leadscore, utm_source, utm_medium, utm_campaign, ownerid, interactions)
- DimDate, DimSource, DimCampaign, DimOwner

## Example KPIs
- MQL to SQL conversion rate
- Lead response time (minutes)
- Campaign ROI = (Attributed Revenue - Spend) / Spend
- Engagement rate by segment

Keep one Date table, use role-playing if needed for Created/Qualified/Closed dates.
