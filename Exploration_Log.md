# NovaTech Q Exploration Log

**Student Name:** 
**Date:**

## Q Exploration Questions

For each question, record Q's answer and cross-check against your dashboard.

| # | Question Asked | Q's Answer (summarize) | Dashboard Visual Used to Cross-Check | Dashboard Shows | Match? | Notes |
|---|---------------|----------------------|--------------------------------------|-----------------|--------|-------|
| 1 | Which campaign channel has the highest conversion rate? | Q identified Partner Referral as the campaign channel with the highest conversion rate.| Marketing Funnel — Funnel Stage by Channel | Direct Mail has the highest conversion rate.| No | Q and the dashboard produced different results. Partner Referral has a high absolute volume of won deals, but conversion rate measures the proportion of wins relative to the total volume. The dashboard calculation identifies Direct Mail as the highest-converting channel.

| 2 | What is the average deal size by company size? |Q reported an overall average Deal Value of 1,590.99 and identified Medium-sized companies as having the highest average Deal Value at 1,655.47.| Sales Pipeline — Revenue by Company Size |Enterprise has the highest average deal value, approximately $1.6K. | No|Q identified a different company-size category as the leader. This may indicate a difference in how Q interpreted or aggregated the deal-size measure. |
| 3 | What is the average resolution time for critical vs. low-priority tickets? |Q reported an overall average Resolution Time of 2.04 days across the critical and low-priority categories. | Customer Health — Resolution Time by Priority | No|The dashboard shows an average of approximately 1.97 days.| The results are close but not identical. The difference may be caused by Q using a different aggregation or interpretation of the resolution-time field.|
| 4 | What are the top 10 accounts by support ticket volume, and what is their total deal revenue? | Q identified the top 10 accounts based on support-ticket volume and reported 1,513 tickets and 39,550,986 in total Deal Value.| Customer Health — At-Risk Accounts table |Yes / Partial|The dashboard shows account-level support-risk information, including the accounts with high ticket volume. | Q provided a combined top-10 ticket count and total deal revenue. The dashboard can be used to cross-check the account-level results, but the exact combined calculation is not directly displayed as one dashboard value.|
| 5 | Are there any campaigns where we spent more than we earned back? |Q identified underperforming campaigns where Campaign ROI was less than or equal to 0. These campaigns had 353,510,938.80 in Campaign Spend versus 25,050,491.47 in Revenue Attributed. | Marketing Funnel — Spend vs. Revenue combo chart | Yes / Partial|The dashboard shows campaigns/channels where Campaign Spend exceeds Revenue Attributed. | Q's overall conclusion agrees with the dashboard: there are campaigns where spending exceeds attributed revenue. The exact aggregate totals from Q are not directly displayed in the combo chart, so the dashboard validates the conclusion rather than the exact totals.|

## Reflection (include in written summary)

- Where did Q agree with the dashboard?
QuickSight Q generally agreed with the dashboard on broader business patterns, particularly when identifying underperforming campaigns where campaign spending exceeded attributed revenue. Q was also able to provide useful summaries of deal value, support-ticket volume, and resolution time that could be compared with the dashboard.

The Topic helped Q understand important NovaTech business terminology and allowed it to answer questions using natural language across the integrated data.
- Where did Q disagree or struggle? Why?
Q disagreed with the dashboard on several questions that required specific calculations or comparisons. For example, Q identified Partner Referral as having the highest campaign conversion rate, while the dashboard identified Direct Mail. Q also identified Medium-sized companies as having the highest average deal value, while the dashboard identified Enterprise companies.

For resolution time, Q returned 2.04 days, compared with approximately 1.97 days in the dashboard.

These differences may result from how Q interpreted the question, selected the relevant fields, or applied aggregation to the underlying data. The results demonstrate that Q answers should be validated against the dashboard, especially for important KPIs and calculated metric
- When would you use Q vs. the dashboard to answer a business question?
QuickSight Q is useful for fast, natural-language exploration and for discovering patterns across CRM, Marketing, and Support data. It allows users to ask questions without manually navigating multiple dashboard visuals.

The dashboard should be used as the primary source for validated business reporting and decision-making because its calculations, filters, and visual definitions are explicitly configured. When Q produces a different result from the dashboard, the dashboard should be used as the reference point and the discrepancy should be investigated.