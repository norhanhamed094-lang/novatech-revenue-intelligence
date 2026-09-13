# NovaTech Data Verification Log

**Student Name:**  Norhan Koshty
**Date:**  09/09/2026

## Instructions

Query each pre-indexed knowledge base using Quick Chat. For each question, record the expected answer (from the data dictionary), Q's actual response, and whether they match. Minimum 6 entries (2 per data knowledge base).

## Verification Log

| # | Knowledge Base | Question Asked | Expected Answer | Q's Actual Answer | Match? | Notes |
|---|----------------|---------------|-----------------|-------------------|--------|-------|
| 1 | NovaTech CRM Deals |How many unique customers are in the crm deals data ?|CRM contains 85 unique accounts | There are 85 unique customers|Yes| |
| 2 | NovaTech CRM Deals |How many records are in the crm deals data ?|499 deals | The novatech_crm_deals.csv dataset contains 499 records in total.|yes | |
| 3 | NovaTech Marketing Campaigns | How many missing household incomes in the marketing data campaigns data?|24 rows have missing incomes|There are 24 records with missing (null) annual_income values in the marketing campaigns dataset, out of 2,240 total records (~1.07%). |yes | |
| 4 | NovaTech Marketing Campaigns |How many Marketing lead and campaign interaction data ? |2240 rows  | The novatech_marketing_campaigns.csv dataset contains a total of 2,240 records of marketing lead and campaign interaction data| yes| |
| 5 | NovaTech Support Tickets |How many Customer support ticket data ? | 3000 records| There are 3,000 customer support tickets in the dataset.novatech_support_...| yes| |
| 6 | NovaTech Support Tickets | How many IDs in the support tickets data are orphans that do not appear in the CRM data? |15 orphan account IDs| That means there are 15 orphan account IDs in the support tickets data that do not appear in the CRM data: ACCT-101 through ACCT-115|yes | |
| 7 | NovaTech Reference Documents | | | | | |

## Cross-Check

Pick one fact from above and confirm it independently in the QuickSight dataset preview.

- **Fact verified:**  CRM contains 499 deals
- **Chat said:** The novatech_crm_deals.csv dataset contains 499 records in total.
- **QuickSight shows:** There are 499 rows in the dataset preview 
- **Consistent?** yes,totally consistent
