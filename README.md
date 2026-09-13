# novatech-revenue-intelligence
NovaTech Revenue Intelligence Dashboard Project
# NovaTech Revenue Intelligence

## Project Overview

NovaTech Revenue Intelligence is a business intelligence project built in **Amazon QuickSight** to provide an integrated view of NovaTech's marketing performance, sales pipeline, and customer health.

The project combines data from three business areas:

- **CRM Deals** – sales opportunities, deal outcomes, revenue, products, regions, and sales representatives.
- **Marketing Campaigns** – campaign spend, attributed revenue, engagement, response rates, and funnel stages.
- **Support Tickets** – customer issues, ticket volume, resolution time, sentiment, and risk indicators.

The goal is to help business leaders identify revenue opportunities, understand sales performance, evaluate marketing effectiveness, and proactively manage customer risk.

---

## Business Objectives

The project focuses on answering key business questions such as:

- Which marketing channels and campaigns perform best?
- Which campaigns generate strong revenue relative to spending?
- What is the overall sales win rate?
- Which products, regions, and customer segments generate the most revenue?
- What are the main reasons for lost deals?
- Which customers have high support activity and potential risk?
- How does customer sentiment relate to support activity?
- How can management use these insights to improve revenue and customer retention?

---

## Data Sources

The analysis uses three datasets.

### 1. CRM Deals

Contains sales opportunity and deal information, including:

- Account ID
- Company name
- Industry
- Company size
- Sales region
- Sales representative
- Product
- Deal stage
- Deal value
- Deal creation and closing dates
- Loss reason

**Records:** 499  
**Won Deals:** 315  
**Lost Deals:** 184

---

### 2. Marketing Campaigns

Contains campaign and customer engagement information, including:

- Account ID
- Campaign name
- Campaign channel
- Campaign date
- Funnel stage
- Customer segment
- Campaign spend
- Attributed revenue
- Campaign response
- Web visits
- Customer engagement metrics

**Records:** 2,240

The observed campaign response rate is approximately **27.2%**.

---

### 3. Support Tickets

Contains customer support and service information, including:

- Account ID
- Ticket ID
- Ticket creation and resolution dates
- Priority
- Product area
- Contact channel
- Customer tier
- Users affected
- Downtime
- Customer sentiment
- Security and data-loss indicators

**Records:** 3,000

---

## Data Integration

The three datasets share the common field:

`account_id`

The CRM dataset was used as the primary dataset. Marketing and Support information was summarized at the account level before integration to reduce one-to-many join duplication and unnecessary row multiplication.

The unified dataset enables account-level analysis across:

**Marketing → Sales → Customer Support**

This allows revenue performance to be evaluated together with customer engagement and customer health.

---

## Data Preparation

Data preparation was performed in Amazon QuickSight.

Key preparation steps included:

- Correcting field data types
- Removing unnecessary technical fields
- Joining datasets using `account_id`
- Creating calculated fields
- Handling null values appropriately
- Summarizing one-to-many datasets at account level before joining

### Calculated Fields

#### Days to Close

```text
dateDiff({deal_created_date}, {deal_closed_date}, 'DD')

Measures the number of days between deal creation and closing.

Discount Percentage
ifelse(
    {deal_stage} = 'Lost',
    null,
    ifelse(
        {list_price} = 0,
        0,
        ({list_price} - {deal_value}) / {list_price}
    )
)

Calculates the discount percentage for won deals.

Deal Size Category
ifelse(
    {deal_value} < 1000,
    'Small',
    {deal_value} < 5000,
    'Medium',
    {deal_value} < 10000,
    'Large',
    'Enterprise'
)

Categorizes deals by value.

Campaign ROI
ifelse(
    {campaign_spend} = 0,
    0,
    ({revenue_attributed} - {campaign_spend}) / {campaign_spend}
)

Measures marketing return relative to campaign spending.

Total Product Spend
{product_spend_tier1} +
{product_spend_tier2} +
{product_spend_tier3}

Combines product spending categories.

Lead Engagement Score
ifelse({campaign_response} = 1, 1, 0) +
ifelse({web_visits_per_month} >= 10, 1, 0) +
ifelse({days_since_last_engagement} <= 30, 1, 0)

Provides a simple measure of customer engagement.

Resolution Time
dateDiff({ticket_created_date}, {ticket_resolved_date}, 'HH')

Calculates support ticket resolution time in hours.

Unresolved tickets remain null rather than being treated as zero.

Dashboard

The final QuickSight dashboard contains three main views.

1. Marketing Funnel

The Marketing Funnel provides visibility into campaign performance and customer engagement.

Key Metrics
Total Campaign Spend
Attributed Revenue
Average Campaign ROI
Campaign Response Rate
Revenue by Channel
Campaign Spend vs. Revenue
Marketing Funnel by Stage
Filters
Campaign Name
Campaign Channel
Campaign Date
Customer Segment
2. Sales Pipeline

The Sales Pipeline provides an overview of sales performance and revenue generation.

Key Metrics
Total Deals
Won Deals
Win Rate
Average Deal Value
Average Days to Close
Revenue by Product
Revenue by Customer Segment
Primary Loss Reasons
Deal Outcomes
Filters
Sales Region
Sales Manager
Product
Deal Creation Date
Deal Stage

Interactive filtering allows users to select deal outcomes and explore the corresponding product and customer-segment performance.

3. Customer Health

The Customer Health view focuses on customer support activity and potential account risk.

Key Metrics and Visuals
Total Support Tickets
Average Resolution Time
Ticket Volume by Account
Tickets by Product Area
Tickets by Customer Sentiment
High-Risk Account Indicators

High-risk accounts are identified using a combination of:

High support ticket volume
Negative customer sentiment
High deal value
Filters
Account
Priority
Product Area
Customer Tier
Region
QuickSight Q

Amazon QuickSight Q was configured to provide natural-language exploration of the business data.

A dedicated Topic named:

NovaTech Revenue Intelligence

was created with business descriptions and synonyms for important fields such as:

Deal Value
Deal Stage
Campaign Spend
Attributed Revenue
Campaign Response
Ticket ID
Customer Sentiment
Account ID
Resolution Time

Technical or unnecessary fields were excluded from the Topic where appropriate.

Q Exploration

Example questions explored using QuickSight Q include:

Which campaign channel has the highest conversion rate?
What is the average deal size by company size?
What is the average resolution time for critical vs. low-priority tickets?
What are the top 10 accounts by support ticket volume and their total deal revenue?
Are there campaigns where spending was greater than attributed revenue?

Q results were cross-checked against dashboard visuals.

Some differences were identified between Q and dashboard calculations, demonstrating the importance of validating AI-generated answers against established dashboard metrics.

For example, Q identified Partner Referral for one conversion-rate question, while the dashboard calculation identified Direct Mail. This difference was documented as part of the Q evaluation.

Key Business Insights
Marketing

The overall campaign response rate is approximately 27.2%, indicating an opportunity to improve campaign engagement through better targeting and messaging.

Campaign spend should be compared with attributed revenue to identify campaigns where investment is not generating sufficient returns.

Sales

The CRM dataset contains 499 deals, with 315 Won and 184 Lost, representing an observed win rate of approximately 63%.

Analyzing successful deals by product, region, customer segment, and sales representative can help identify repeatable patterns for improving future opportunities.

Customer Health

High ticket volume combined with negative sentiment and high-value accounts can indicate customers that require proactive attention.

These accounts should be prioritized for customer-success outreach and issue resolution to reduce potential churn and revenue loss.

Recommendations

Based on the analysis, NovaTech should:

Optimize underperforming marketing campaigns by reviewing campaigns where spending exceeds attributed revenue.
Improve campaign engagement by investigating low-response channels and refining targeting.
Analyze successful sales patterns across products, regions, and customer segments.
Review major loss reasons to identify opportunities to improve sales conversion.
Prioritize high-risk customers using support volume, sentiment, and account value.
Use QuickSight Q for exploration, while validating important business decisions against trusted dashboard metrics.
Project Deliverables

The project includes:

Amazon QuickSight dashboard
Marketing Funnel view
Sales Pipeline view
Customer Health view
Unified dataset
Data preparation and transformation documentation
QuickSight Q Topic
Q baseline and post-Topic testing
Q Exploration Log
Verification Log
Dashboard annotations
Executive report
Dashboard PDF export
Supporting screenshots
Tools & Technologies
Amazon QuickSight
QuickSight SPICE
QuickSight Q
CSV datasets
Data integration and calculated fields
Interactive dashboards and filters
Project Structure
novatech-revenue-intelligence/
│
├── README.md
│
├── data/
│   ├── novatech_crm_deals.csv
│   ├── novatech_marketing_campaigns.csv
│   └── novatech_support_tickets.csv
│
├── dashboard/
│   └── dashboard-export.pdf
│
├── screenshots/
│   ├── join-diagram.png
│   ├── data-preparation.png
│   ├── marketing-funnel.png
│   ├── sales-pipeline.png
│   ├── customer-health.png
│   ├── q-baseline.png
│   ├── q-topic.png
│   └── annotated-dashboard.png
│
└── report/
    ├── executive-report.pdf
    ├── q-exploration-log.md
    └── verification-log.md
Conclusion

The NovaTech Revenue Intelligence project demonstrates how CRM, Marketing, and Support data can be integrated into a single business intelligence solution.

The resulting dashboard provides executives with a clear view of:

Marketing Performance → Sales Performance → Customer Health

while QuickSight Q provides an additional natural-language interface for business exploration.

Together, these capabilities support more informed decisions around revenue growth, marketing investment, sales performance, and customer retention.
