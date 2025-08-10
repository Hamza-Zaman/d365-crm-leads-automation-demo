# Segmentation Rules (Customer Insights – Journeys)

- High Intent: LeadScore >= 70 AND utm_medium = "cpc"
- Warm: LeadScore between 40 and 69 AND consent = True
- Dormant: No interaction in last 90 days
- Enterprise Manufacturing: Industry in {"Manufacturing","Construction","Utilities"} AND employee_count > 250
