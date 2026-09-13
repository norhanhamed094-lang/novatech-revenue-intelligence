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
