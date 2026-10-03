# Retail Customer Segmentation Using RFM Analysis

Not every customer is worth the same to a business. Some buy often and bring in most of the revenue. Others bought once and never came back.

In this project I took a year of retail transactions and sorted customers into groups based on how they buy. I used **RFM analysis** (Recency, Frequency, Monetary) in **Python and Pandas**, then built an interactive **Power BI dashboard** to show the results.

The goal was simple: turn raw transaction rows into something a marketing or retention team could actually act on.

---

## Table of Contents

- [The Business Problem](#the-business-problem)
- [Dataset](#dataset)
- [Data Cleaning](#data-cleaning)
- [How RFM Works](#how-rfm-works)
- [Results](#results)
- [Key Insights](#key-insights)
- [Power BI Dashboard](#power-bi-dashboard)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [Tools Used](#tools-used)
- [Project Structure](#project-structure)
- [What I Learned](#what-i-learned)
- [About Me](#about-me)

---

## The Business Problem

A retailer has years of transaction data, but a list of transactions doesn't tell you who your best customers are, who is drifting away, or who is already gone.

Without that, every customer gets the same emails and the same offers, even though their behavior and value are very different.

I set out to answer these questions:

- Who are the highest-value customers?
- Who buys most often?
- Who bought recently?
- How much revenue comes from the top customers?
- Who is at risk of leaving?
- Who has already left?
- Who could become a loyal customer with a little push?
- How should each group be approached?

---

## Dataset

I used the **UCI Online Retail Dataset**.

- **541,909** transaction records
- Period: **1 December 2010 to 9 December 2011**

| Column | What it holds |
|---|---|
| `InvoiceNo` | Invoice number |
| `StockCode` | Product code |
| `Description` | Product name |
| `Quantity` | Items bought |
| `InvoiceDate` | Date and time of the purchase |
| `UnitPrice` | Price per item |
| `CustomerID` | Unique customer ID |
| `Country` | Customer's country |

### Problems in the raw data

- **135,080** rows had no `CustomerID`
- **1,454** rows had no `Description`
- **5,268** rows were duplicates
- Cancellations and returns were mixed in with normal sales

The missing `CustomerID` values mattered most. This is a customer-level analysis, and a transaction with no customer attached can't be used.

---

## Data Cleaning

Steps, in order:

1. Dropped rows with no `CustomerID`
2. Removed duplicate rows
3. Removed cancelled orders and negative-quantity rows
4. Converted `InvoiceDate` to a proper datetime
5. Created a `Revenue` column
6. Rolled everything up to one row per customer

Revenue was calculated like this:

```text
Revenue = Quantity × UnitPrice
```

---

## How RFM Works

RFM looks at each customer from three angles.

| Metric | Question it answers | How I measured it | Good looks like |
|---|---|---|---|
| **Recency** | How recently did they buy? | Reference date minus their last purchase date | Low number |
| **Frequency** | How often do they buy? | Number of invoices | High number |
| **Monetary** | How much do they spend? | Total revenue from that customer | High number |

Each customer gets a score on all three, and the combined scores decide which segment they fall into.

```text
Transactions → Cleaning → Customer-level data → R, F, M → Scores → Segments → Insights
```

<!-- TODO: add how you scored (quintiles? fixed bins?), the reference date you used, and the rule for each segment. -->

---

## Results

### Overall numbers

| Metric | Value |
|---|---|
| Total customers | 4,338 |
| Total orders | 18,532 |
| Total revenue | 8.89M |
| Average revenue per customer | 2,049 |
| Average recency | 92.54 days |
| Average frequency | 4.27 orders |

### Customer segments

| Segment | Customers | % of customers | Revenue | % of revenue |
|---|---:|---:|---:|---:|
| Champions | 942 | 21.72% | 5.74M | 64.56% |
| Loyal Customers | 460 | 10.60% | 910.76K | 10.25% |
| At-Risk Customers | 661 | 15.24% | 823.91K | 9.27% |
| Potential Loyalists | 511 | 11.78% | 508.60K | 5.72% |
| Lost Customers | 1,074 | 24.76% | 523.80K | 5.89% |
| Other | 690 | 15.91% | 382.18K | 4.30% |

---

## Key Insights

### 1. A small group drives most of the revenue

Champions are about **22% of customers** but bring in about **65% of revenue** (roughly 5.74M). If this group slips, the business feels it immediately.

### 2. The At-Risk group has real money behind it

There are **661 At-Risk customers** with about **824K** in past revenue. They used to matter and their activity is dropping. They are the best target for win-back campaigns.

Two examples from the data:

| Customer ID | Recency | Frequency | Monetary |
|---|---:|---:|---:|
| 15749 | 235 days | 3 | 44,534 |
| 15098 | 182 days | 3 | 39,917 |

Both have spent a lot but have gone quiet. A customer like this needs a very different approach from someone who only ever spent a small amount.

### 3. Lost Customers are the biggest segment

**1,074 customers (24.76%)** are Lost. Their average recency is about 217 days, and their average frequency is just **1.10 orders**. Most of them bought once and never returned, so this is as much a first-purchase problem as a retention problem.

### 4. Potential Loyalists are the easiest growth opportunity

**511 customers** bought very recently (about 16 days ago on average) but only about 2 times. They are already warm. The job is to get them to order a third and fourth time.

---

## Power BI Dashboard

I built the dashboard as **Retail Customer Intelligence: Executive Overview | RFM & Customer Behavior**. It has four sections:

**Executive Overview**
- Total customers, orders, revenue, and average revenue per customer
- Monthly revenue trend

**RFM Analysis**
- Average recency, frequency, and monetary value
- Top customers by revenue and by frequency
- RFM customer value matrix

**Customer Segmentation**
- Customers and revenue by segment
- Revenue contribution
- Average RFM values per segment

**Retention & Risk**
- At-Risk and Lost customer counts and revenue
- Top At-Risk customers by monetary value
- Average recency by segment

### Preview

![Retail Customer Intelligence Dashboard](images/dashboard.png)

You can also open the full dashboard here: [Retail_Customer_Segmentation_RFM.pdf](dashboard/Retail_Customer_Segmentation_RFM.pdf)

---

## Recommendations

| Segment | What I'd do |
|---|---|
| **Champions** | Protect them. VIP perks, early access, exclusive rewards, personal offers. |
| **Loyal Customers** | Raise how often they buy through cross-sells and personalized recommendations. |
| **At-Risk Customers** | Run win-back campaigns built around what they bought before. Start with the highest spenders. |
| **Potential Loyalists** | Push for repeat purchases with follow-up offers soon after their latest order. |
| **Lost Customers** | Don't spend on everyone. Reactivate only those with meaningful past value. |
| **Other** | Keep watching. Look for customers who start moving into higher segments. |

The point is to stop treating every customer the same way.

---

## Limitations

Worth knowing before you rely on these numbers:

- **About a quarter of the raw rows were dropped** because they had no `CustomerID`. The analysis only covers identified customers.
- **Returns and cancellations were excluded**, so revenue reflects gross sales, not net.
- **The data covers about one year**, so "Lost" means inactive in this window, not necessarily gone for good.
- **Segment rules are my own choices.** Different cut-offs would move customers between groups.
- **The dataset comes from a single UK-based online retailer**, and many of its buyers appear to be businesses rather than individuals. Results may not carry over to a typical consumer shop.

---

## Tools Used

- **Python** for cleaning, transformation, revenue calculation, RFM, and segmentation
- **Pandas** for aggregation, filtering, and grouping
- **Power BI** for KPIs, segment charts, and the interactive dashboard

---

## Project Structure

```text
Retail-Customer-Segmentation-RFM/
│
├── data/
│   └── Online Retail.xlsx
│
├── notebook/
│   └── Retail_Customer_Segmentation_RFM.ipynb
│
├── dashboard/
│   └── Retail_Customer_Segmentation_RFM.pdf
│
├── images/
│   └── dashboard.png
│
└── README.md
```

---

## What I Learned

This project pushed me past making charts and into the full workflow:

- Working with messy, real transaction data
- Finding and fixing data quality problems
- Building business metrics from raw rows
- Applying RFM and building segments
- Turning numbers into recommendations a business can use
- Presenting results in a clear Power BI dashboard

---

## About Me

**Tushar**
Data Analyst | Python | SQL | Power BI | Excel
