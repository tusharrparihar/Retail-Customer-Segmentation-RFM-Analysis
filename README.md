## 🛍️ Retail Customer Segmentation & RFM Analysis</h1>

  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" alt="Python"></a>
  <a href="https://powerbi.microsoft.com/"><img src="https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi" alt="Power BI"></a>
  <a href="https://jupyter.org/"><img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter" alt="Jupyter Notebook"></a>
  <a href="https://pandas.pydata.org/"><img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas" alt="Pandas"></a>
</p>

> A customer analytics project using transaction data, exploratory analysis, RFM scoring, customer segmentation, and Power BI to identify high-value, loyal, potential, at-risk, and inactive customers.

  <b>🏆 4,338 Customers</b> &nbsp;|&nbsp; <b>🧾 18,532 Orders</b> &nbsp;|&nbsp; <b>💰 8.89M Revenue</b> &nbsp;|&nbsp; <b>👑 Champions = 64.56% of Revenue</b>
</p>

---

## 📌 Project Overview

This project analyzes historical online retail transactions to understand **customer purchasing behavior and customer value**.

The main challenge is that a large transaction dataset does not directly show which customers are most valuable, which customers are highly engaged, and which customers may be at risk of becoming inactive.

The project addresses this using:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Customer-level revenue analysis
- Recency, Frequency, and Monetary (RFM) analysis
- RFM-based customer segmentation
- Python analysis and visualizations
- An interactive Power BI dashboard
- Business-focused recommendations

The final analysis contains **4,338 customers, 18,532 orders, and 8.89M in total revenue**. The strongest finding is that **Champions represent 21.72% of customers but contribute 64.56% of total revenue**.

---

## 📊 Dashboard Preview

<!-- TODO: Add a Power BI dashboard screenshot here, for example: assets/dashboard_overview.png -->

<p align="center">
<img width="979" height="552" alt="Retail Customer Intelligence" src="https://github.com/user-attachments/assets/5e3a467b-ceda-4a76-a18f-bac249932245" />

### 🖥️ Dashboard

<!-- TODO: Add the Power BI Public/Service dashboard link here if available -->

**📄 Dashboard PDF:** [`Retail_Customer_Segmentation_RFM.pdf`](./Visuals/Retail_Customer_Segmentation_RFM.pdf)

---

## 🧭 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Project Objectives](#-project-objectives)
- [Business Questions](#-business-questions)
- [Dataset Overview](#-dataset-overview)
- [Data Structure](#-data-structure)
- [Data Cleaning & Preprocessing](#-data-cleaning--preprocessing)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [RFM Analysis](#-rfm-analysis)
- [Customer Segmentation](#-customer-segmentation)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Key Insights](#-key-insights)
- [Business Recommendations](#-business-recommendations)
- [Project Workflow](#-project-workflow)
- [Tools & Technologies](#-tools--technologies)
- [Project Files](#-project-files)
- [How to Reproduce the Analysis](#-how-to-reproduce-the-analysis)
- [Processed Outputs](#-processed-outputs)
- [Project Snapshot](#-project-snapshot)
- [Conclusion](#-conclusion)
- [Project Links](#-project-links)
- [Author](#-author)

---

## 💼 Business Problem

The retail business has a large volume of historical transaction data but lacks a structured way to understand differences in customer purchasing behavior and customer value.

Without identifying high-value, loyal, emerging, inactive, and at-risk customers, it becomes difficult to focus retention and customer engagement efforts on the groups that contribute most to revenue.

This project uses RFM analysis to turn transaction-level data into **customer-level metrics and behavioral segments** that can support:

- Customer retention
- Loyalty initiatives
- Targeted marketing
- Repeat purchasing
- Revenue-focused customer management

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 🎯 Project Objectives

The project aims to:

1. Analyze customer transaction behavior.
2. Quantify customer value using RFM analysis.
3. Segment customers based on their purchasing characteristics.
4. Identify high-value, loyal, emerging, at-risk, and inactive customers.
5. Understand revenue concentration across customer segments.
6. Identify opportunities for customer retention and repeat purchasing.
7. Support differentiated customer engagement and marketing strategies.

---

## ❓ Business Questions

The analysis focuses on questions such as:

- Which customers generate the highest monetary value?
- Which customers purchase most recently and most frequently?
- How concentrated is revenue among high-value customers?
- What are the Recency, Frequency, and Monetary characteristics of the customer base?
- How can customers be scored and compared using RFM?
- Which customer segments contribute the most revenue?
- Which customers or segments show characteristics associated with inactivity or retention risk?
- Which segments represent opportunities for strengthening loyalty and repeat purchasing?
- How can customer segments support differentiated retention and engagement strategies?

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 🗂 Dataset Overview

The project uses the **UCI Online Retail Dataset**, containing transactional data from an online retail business.

The original dataset contains:

| 📋 Attribute | Value |
|---|---:|
| Transaction records | 541,909 |
| Columns | 8 |
| Data period | 1 Dec 2010 – 9 Dec 2011 |
| Missing CustomerID values | 135,080 |
| Missing Description values | 1,454 |
| Duplicate records | 5,268 |

The transaction-level data contains customer, product, transaction, pricing, geographic, and timestamp information.

<!-- TODO: Add the original dataset source link if you want to provide the external UCI dataset reference. -->

---

## 🧱 Data Structure

The original dataset contains the following fields:

| Column | Description |
|---|---|
| `InvoiceNo` | Transaction / invoice ID |
| `StockCode` | Product ID |
| `Description` | Product name |
| `Quantity` | Number of items purchased |
| `InvoiceDate` | Purchase date and time |
| `UnitPrice` | Price per item |
| `CustomerID` | Unique customer ID |
| `Country` | Customer location |

A `Revenue` column was created during preprocessing:

```text
Revenue = Quantity × UnitPrice
```

This revenue value was then aggregated at customer level for RFM analysis.

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 🧹 Data Cleaning & Preprocessing

The raw dataset required several cleaning steps before customer-level analysis.

<details>
<summary><b>🧼 Cleaning steps (click to expand)</b></summary>

1. ✅ Removed records with missing CustomerID.
2. ✅ Removed duplicate transaction records.
3. ✅ Removed cancelled invoices.
4. ✅ Removed transactions with negative quantities.
5. ✅ Converted InvoiceDate to datetime format.
6. ✅ Removed transactions with non-positive UnitPrice.
7. ✅ Recalculated Revenue using Quantity × UnitPrice.
8. ✅ Created a cleaned transaction-level dataset.
9. ✅ Aggregated transactions at customer level for RFM analysis.

</details>

> ℹ️ Description values were not required for RFM calculations, so missing descriptions were retained when the transaction was otherwise valid.

### ✨ Final cleaned transaction dataset

The processed transaction file contains:

- **392,692 transaction records**
- **9 columns**, including the calculated Revenue field

<details>
<summary><b>📑 View the 9 columns</b></summary>

- `InvoiceNo`
- `StockCode`
- `Description`
- `Quantity`
- `InvoiceDate`
- `UnitPrice`
- `CustomerID`
- `Country`
- `Revenue`

</details>

---

## 🔎 Exploratory Data Analysis

EDA was performed in Python to understand overall sales, customer behavior, product performance, geographic contribution, and revenue trends.

### 📌 Overall KPIs

| Metric | Value |
| --- | --- |
| Total Revenue | 8.89M |
| Total Customers | 4,338 |
| Total Orders | 18,532 |
| Total Products | 3,665 |
| Total Units Sold | 5,152,002 |
| Average Order Value | 479.56 |
| Average Customer Revenue | 2,048.69 |

The RFM dashboard reports the average customer revenue as **2,049**.

### 👤 Customer analysis

The notebook analyzes:

- Top customers by revenue
- Distribution of customer revenue
- Cumulative revenue concentration
- Top customers by purchasing frequency
- Most recent customers
- Highest-spending customers

The top five customers by revenue were:

| 🏅 Customer ID | Revenue |
| --- | --- |
| 14646 | 280.21K |
| 18102 | 259.66K |
| 17450 | 194.39K |
| 16446 | 168.47K |
| 14911 | 143.71K |

### 🌍 Geographic analysis

Revenue by country was also examined.

The highest-revenue countries were:

| 🌐 Country | Revenue |
| --- | --- |
| 🇬🇧 United Kingdom | 7.29M |
| 🇳🇱 Netherlands | 285.45K |
| 🇮🇪 EIRE | 265.26K |
| 🇩🇪 Germany | 228.68K |
| 🇫🇷 France | 208.93K |

The **United Kingdom** is the largest revenue-generating market in the analyzed data.

### 📅 Time-based analysis

The notebook also examines:

- Monthly revenue
- Monthly order volume
- Monthly active customers
- Monthly average order value

These were used to understand changes in sales activity over the transaction period.

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 📐 RFM Analysis

RFM analysis converts transaction history into three customer-level measures.

| 🔤 Metric | Definition | Interpretation |
| --- | --- | --- |
| ⏱️ **Recency** | Days since the customer's most recent purchase | 🔽 Lower is better |
| 🔁 **Frequency** | Number of unique invoices | 🔼 Higher is better |
| 💰 **Monetary** | Total revenue generated by the customer | 🔼 Higher is better |

### ⏱️ Recency

```text
Recency = Reference Date − Most Recent Purchase Date
```

The reference date in the notebook is calculated as one day after the latest transaction date.

### 🔁 Frequency

```text
Frequency = Number of Unique Invoices
```

### 💰 Monetary

```text
Monetary = Sum of Revenue
```

The notebook calculates RFM scores using five quantile groups:

- ⏱️ Recency is scored in reverse order, because a lower number of days indicates more recent activity.
- 🔁 Frequency is scored from lower to higher purchasing frequency.
- 💰 Monetary is scored from lower to higher customer revenue.

The resulting fields are:

- `R_Score`
- `F_Score`
- `M_Score`
- `RFM_Score`

A combined RFM_Total was also calculated during the notebook analysis.

---

## 👥 Customer Segmentation

Customers were assigned to six behavioral segments using the RFM scores.

The segmentation logic implemented in the notebook is:

```text
Champions
    R >= 4 and F >= 4 and M >= 4

Loyal Customers
    R >= 3 and F >= 4 and M >= 3

Potential Loyalists
    R >= 4 and F >= 2

At-Risk Customers
    R <= 2 and F >= 3

Lost Customers
    R <= 2 and F <= 2

Other
    Remaining customers
```

### 📋 Segment Summary

| Segment | Customers | % of Customers | Revenue | % of Revenue | Avg. Recency | Avg. Frequency | Avg. Monetary |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 🏆 **Champions** | 942 | 21.72% | 5.74M | 64.56% | 12.50 | 11.20 | 6,091.24 |
| 💙 **Loyal Customers** | 460 | 10.60% | 910.76K | 10.25% | 38.45 | 5.29 | 1,979.91 |
| ⚠️ **At-Risk Customers** | 661 | 15.24% | 823.91K | 9.27% | 150.64 | 3.41 | 1,246.46 |
| 🌱 **Potential Loyalists** | 511 | 11.78% | 508.60K | 5.72% | 16.41 | 2.12 | 995.31 |
| 🔘 **Other** | 690 | 15.91% | 382.18K | 4.30% | 45.34 | 1.49 | 553.89 |
| 💤 **Lost Customers** | 1,074 | 24.76% | 523.80K | 5.89% | 216.68 | 1.10 | 487.71 |

### 🔍 Segment characteristics

> 👇 Click each segment to expand it.

<details>
<summary>🏆 <strong>Champions</strong></summary>

Champions are the highest-value and most engaged customer group.

- 942 customers
- 21.72% of customers
- 64.56% of revenue
- Average recency: 12.50 days
- Average frequency: 11.20 orders
- Average monetary value: 6,091.24

</details>

<details>
<summary>💙 <strong>Loyal Customers</strong></summary>

Customers showing relatively consistent purchasing behavior.

- 460 customers
- 10.60% of customers
- 10.25% of revenue
- Average recency: 38.45 days
- Average frequency: 5.29 orders
- Average monetary value: 1,979.91

</details>

<details>
<summary>⚠️ <strong>At-Risk Customers</strong></summary>

Customers who have generated meaningful historical value but show reduced recent engagement.

- 661 customers
- 15.24% of customers
- 9.27% of revenue
- Average recency: 150.64 days
- Average frequency: 3.41 orders
- Average monetary value: 1,246.46

</details>

<details>
<summary>🌱 <strong>Potential Loyalists</strong></summary>

Customers who have purchased recently but have not yet developed high purchasing frequency.

- 511 customers
- 11.78% of customers
- 5.72% of revenue
- Average recency: 16.41 days
- Average frequency: 2.12 orders
- Average monetary value: 995.31

</details>

<details>
<summary>🔘 <strong>Other Customers</strong></summary>

Customers with comparatively lower purchasing frequency and monetary contribution.

- 690 customers
- 15.91% of customers
- 4.30% of revenue
- Average recency: 45.34 days
- Average frequency: 1.49 orders
- Average monetary value: 553.89

</details>

<details>
<summary>💤 <strong>Lost Customers</strong></summary>

Customers showing very low recent engagement and purchasing frequency.

- 1,074 customers
- 24.76% of customers
- 5.89% of revenue
- Average recency: 216.68 days
- Average frequency: 1.10 orders
- Average monetary value: 487.71

</details>

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 📈 Power BI Dashboard

The Power BI dashboard, titled **Retail Customer Intelligence**, presents the analysis in four main areas.

<details>
<summary><b>1️⃣ Executive Overview</b></summary>

The overview provides:

- Total customers
- Total orders
- Total revenue
- Average customer revenue
- Monthly revenue trend
- Analysis date range

</details>

<details>
<summary><b>2️⃣ Customer Value Analysis</b></summary>

This section focuses on RFM and high-value customers:

- Average Recency
- Average Frequency
- Average Monetary
- Top 10 customers by revenue
- Top 10 customers by frequency
- Recent customers
- RFM Customer Value Matrix

</details>

<details>
<summary><b>3️⃣ Customer Segmentation</b></summary>

The segmentation page shows:

- Customer count by segment
- Revenue by segment
- Revenue contribution
- Average Monetary by segment
- Average Recency by segment
- Average Frequency by segment

</details>

<details>
<summary><b>4️⃣ Retention & Risk Analysis</b></summary>

The retention page focuses on:

- At-Risk customer count
- Lost customer count
- At-Risk revenue
- Lost revenue
- Recency vs Monetary analysis
- Top At-Risk customers by monetary value
- Average recency by segment

</details>

The dashboard covers the transaction period from **1 December 2010 to 9 December 2011**.

---

## 💡 Key Insights

### 1️⃣ 👑 Champions drive most of the revenue

Champions represent only **21.72% of customers**, but contribute **64.56% of total revenue**, approximately **5.74M**.

They also have:

- Average recency: 12.50 days
- Average frequency: 11.20 orders
- Average monetary value: 6,091.24

This shows a strong concentration of revenue among highly engaged customers.

### 2️⃣ ⚠️ A significant customer group is at risk

There are **661 At-Risk customers**, representing **15.24% of the customer base** and approximately **824K in revenue**.

Their average recency is **150.64 days**, indicating substantially lower recent engagement than the active customer segments.

### 3️⃣ 💤 Lost Customers are the largest segment

Lost Customers contain **1,074 customers**, or **24.76% of the customer base**.

Their:

- Average recency is 216.68 days
- Average frequency is 1.10 orders
- Average monetary value is 487.71

This represents a substantial inactive customer population.

### 4️⃣ 📊 Revenue is highly concentrated

Champions account for roughly one-fifth of customers but generate almost two-thirds of revenue.

This makes retention of high-value customers particularly important because changes in their purchasing behavior could have a significant effect on overall revenue.

### 5️⃣ 🌱 Potential Loyalists are a growth opportunity

There are **511 Potential Loyalists**, representing **11.78% of customers**.

Their average recency is only **16.41 days**, showing recent engagement, while their average frequency is **2.12 orders**.

This creates an opportunity to encourage more frequent purchases and develop stronger loyalty.

### 6️⃣ 🚨 High-value At-Risk customers should be prioritized

Not all At-Risk customers have the same business value.

Examples from the analysis include:

| 🆔 Customer ID | Recency | Frequency | Monetary |
| --- | ---: | ---: | ---: |
| 15749 | 235 | 3 | 44,534 |
| 15098 | 182 | 3 | 39,917 |

These customers have relatively high historical monetary value despite being classified as At-Risk.

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 🧠 Business Recommendations

The recommendations are based directly on the customer segments identified through RFM analysis.

| Segment | 🎬 Recommended Action |
| --- | --- |
| 🏆 **Champions** | Retain through loyalty rewards, personalized offers, VIP benefits, early access, and exclusive rewards. |
| 💙 **Loyal Customers** | Increase purchase frequency through cross-selling, personalized recommendations, and loyalty incentives. |
| ⚠️ **At-Risk Customers** | Launch targeted win-back campaigns based on previous purchases and customer value. |
| 🌱 **Potential Loyalists** | Encourage repeat purchases using personalized recommendations and limited-time offers. |
| 💤 **Lost Customers** | Use selective reactivation campaigns, prioritizing customers with higher historical monetary value. |
| 🔘 **Other** | Use targeted engagement campaigns to identify customers with potential to move into higher-value segments. |

### 🥇 Priority 1 — Protect high-value customers

Champions generate **64.56% of total revenue**, so maintaining their engagement should be a major retention priority.

Possible actions include:

- 👑 VIP benefits
- 🎯 Personalized offers
- 🎁 Loyalty rewards
- ⏰ Early access
- 💎 Exclusive rewards

### 🥈 Priority 2 — Recover valuable At-Risk customers

The At-Risk segment represents approximately **824K in revenue**.

Rather than treating all 661 At-Risk customers equally, retention efforts can prioritize customers based on:

- 💰 Historical monetary value
- 🔁 Previous purchase frequency
- ⏱️ Recency

This provides a more focused approach to win-back campaigns.

### 🥉 Priority 3 — Develop Potential Loyalists

Potential Loyalists are already relatively recent customers but have lower purchase frequency.

Recommended actions include:

- 🛍️ Personalized product recommendations
- ⌛ Limited-time offers
- 🔁 Repeat-purchase incentives
- 🧩 Relevant cross-selling

---

## 🔄 Project Workflow

<details open>
<summary><b>🗺️ View the workflow (click to collapse)</b></summary>

```text
Raw Online Retail Dataset
          │
          ▼
Data Understanding
          │
          ▼
Data Quality Assessment
          │
          ▼
Data Cleaning & Preprocessing
          │
          ├── Missing CustomerID
          ├── Duplicate records
          ├── Cancelled invoices
          ├── Negative quantities
          └── Invalid UnitPrice
          │
          ▼
Revenue Calculation
Quantity × UnitPrice
          │
          ▼
Exploratory Data Analysis
          │
          ├── Customer analysis
          ├── Product analysis
          ├── Country analysis
          └── Monthly trends
          │
          ▼
Customer-Level Aggregation
          │
          ▼
RFM Calculation
          │
          ├── Recency
          ├── Frequency
          └── Monetary
          │
          ▼
RFM Scoring
          │
          ▼
Customer Segmentation
          │
          ├── Champions
          ├── Loyal Customers
          ├── Potential Loyalists
          ├── At-Risk Customers
          ├── Lost Customers
          └── Other
          │
          ▼
Business Insights & Recommendations
          │
          ▼
Power BI Dashboard
```

</details>

---

## 🛠 Tools & Technologies

| 🧰 Tool / Technology | Purpose |
| --- | --- |
| 🐍 **Python** | Data analysis and RFM modeling |
| 🐼 **Pandas** | Data manipulation and aggregation |
| 🔢 **NumPy** | Numerical operations |
| 📉 **Matplotlib** | Data visualization |
| 🎨 **Seaborn** | Exploratory visualization |
| 📓 **Jupyter Notebook** | Analysis workflow |
| 📊 **Power BI Desktop** | Interactive dashboard and reporting |
| 📗 **Excel** | Original transaction dataset |
| 📄 **CSV** | Processed datasets |

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 📁 Project Files

The project materials provided for this analysis are:

<details open>
<summary><b>🌲 Folder structure (click to collapse)</b></summary>

```text
Retail Customer Segmentation & RFM Analysis/
│
├── README.md
│
├── Retail_Customer_Segmentation_RFM.pbix
├── Retail_Customer_Segmentation_RFM(1).pdf
│
├── Customer_Segmentation_RFM_Analysis(1).ipynb
├── Customer_Segmentation_RFM_Analysis.docx
├── Insights & Recommendations.docx
│
├── Online Retail(1).xlsx
│
├── transactions_clean.csv
└── customer_rfm_final.csv
```

</details>

### 📝 File descriptions

| 📄 File | Purpose |
| --- | --- |
| 📗 Online Retail(1).xlsx | Original raw transaction dataset |
| 🧹 transactions_clean.csv | Cleaned transaction-level dataset with calculated Revenue |
| 👥 customer_rfm_final.csv | Final customer-level RFM dataset and segment assignments |
| 📓 Customer_Segmentation_RFM_Analysis(1).ipynb | Python data cleaning, EDA, RFM analysis, segmentation, and analysis |
| 📊 Retail_Customer_Segmentation_RFM.pbix | Power BI dashboard source file |
| 📄 Retail_Customer_Segmentation_RFM(1).pdf | PDF export of the Power BI dashboard |
| 📘 Customer_Segmentation_RFM_Analysis.docx | Business problem, objectives, data understanding, methodology, insights, and recommendations |
| 📘 Insights & Recommendations.docx | Final business insights and recommended actions |

<!-- TODO: Update the folder structure if these files are placed inside different repository folders. -->

---

## ▶ How to Reproduce the Analysis

### 1️⃣ Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_NAME>
```

<!-- TODO: Replace the repository URL with your actual GitHub repository URL. -->

### 2️⃣ Install the Python dependencies

The notebook uses:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

Install them with:

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### 3️⃣ Open the notebook

Open:

```text
Customer_Segmentation_RFM_Analysis(1).ipynb
```

using Jupyter Notebook or JupyterLab.

### 4️⃣ Update the dataset path

The original notebook uses a local Windows path for the raw dataset. For example:

```python
path = Path(r'F:\Portfollio Projects\Customer Segmentation & RFM Analysis\Dataset\Raw Dataset')
```

For a GitHub clone, change this to the location of the dataset in your repository.

For example:

```python
path = Path('./data/raw')
```

<!-- TODO: Update this example if you organize the repository into different data folders. -->

### 5️⃣ Run the notebook

Run the notebook from top to bottom to reproduce:

- ✅ Data quality checks
- ✅ Data cleaning
- ✅ Revenue calculation
- ✅ EDA
- ✅ Customer-level aggregation
- ✅ RFM metrics
- ✅ RFM scoring
- ✅ Customer segmentation
- ✅ Segment-level analysis
- ✅ Export of the processed datasets

### 6️⃣ Explore the Power BI dashboard

Open:

```text
Retail_Customer_Segmentation_RFM.pbix
```

in Power BI Desktop.

The dashboard can then be used to explore customer value, customer segments, and retention risk.

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>

---

## 📦 Processed Outputs

The analysis produces two important processed datasets.

### 🧹 `transactions_clean.csv`

Transaction-level data after cleaning and revenue calculation.

<details>
<summary><b>📑 View columns</b></summary>

- `InvoiceNo`
- `StockCode`
- `Description`
- `Quantity`
- `InvoiceDate`
- `UnitPrice`
- `CustomerID`
- `Country`
- `Revenue`

</details>

### 👥 `customer_rfm_final.csv`

Customer-level RFM output containing:

<details>
<summary><b>📑 View columns</b></summary>

- `CustomerID`
- `Recency`
- `Frequency`
- `Monetary`
- `R_Score`
- `F_Score`
- `M_Score`
- `RFM_Score`
- `Segment`

</details>

The final RFM dataset contains **4,338 customers**.

---

## 📊 Project Snapshot

| 📌 KPI | Result |
| --- | ---: |
| 🧾 Original transactions | 541,909 |
| 🧹 Cleaned transactions | 392,692 |
| 👥 Final customers | 4,338 |
| 🛒 Orders | 18,532 |
| 💰 Revenue | 8.89M |
| 👤 Average customer revenue | 2,049 |
| 🏆 Champions | 942 |
| ⚠️ At-Risk customers | 661 |
| 🌱 Potential Loyalists | 511 |
| 💤 Lost Customers | 1,074 |
| 👑 Champions' revenue contribution | 64.56% |

---

## 🏁 Conclusion

This project shows how transaction-level retail data can be converted into a customer-level view of value and engagement.

The RFM analysis highlights a clear difference between customer groups:

- 🏆 **Champions** are the most valuable segment and generate the majority of revenue.
- ⚠️ **At-Risk Customers** represent a meaningful amount of historical revenue that may be worth targeting with focused win-back campaigns.
- 💤 **Lost Customers** form the largest customer segment by count.
- 🌱 **Potential Loyalists** show recent engagement but lower purchase frequency, creating an opportunity to develop stronger purchasing habits.

The main business priority from the analysis is therefore to **protect high-value Champions, prioritize high-value At-Risk customers for retention, and develop Potential Loyalists into more frequent customers**.

The combination of Python-based analysis and Power BI reporting turns the raw transaction data into a more practical view of customer value, segmentation, and retention opportunities.

---

## 🔗 Project Links

- 🐙 **GitHub Repository:** <!-- TODO: Add GitHub repository link -->
- 📓 **Jupyter Notebook:** [`Customer_Segmentation_RFM_Analysis(1).ipynb`](./Notebook/Customer_Segmentation_RFM_Analysis.ipynb)
- 📄 **Dashboard PDF:** [`Retail_Customer_Segmentation_RFM(1).pdf`](./Visuals/Retail_Customer_Segmentation_RFM.pdf)
- 🧹 **Cleaned Dataset:** [`transactions_clean.csv`](./Dataset/Processed_Dataset/transactions_clean.csv)
- 👥 **Customer RFM Dataset:** [`customer_rfm_final.csv`](./Dataset/Processed_Dataset/customer_rfm_final.csv)
- 📗 **Raw Dataset:** [`Online Retail(1).xlsx`](./Dataset/Raw_Dataset/Online_Retai.xlsx)

---

## 👤 Author

**Tushar**

<!-- TODO: Add your LinkedIn profile link -->

- 💼 LinkedIn: https://www.linkedin.com/in/tusharrparihar

<!-- TODO: Add your email address or portfolio website if you want recruiters to contact you directly. -->

- 🌐 Portfolio / Contact: tusharrparihar@gmail.com

<p align="right"><a href="#-retail-customer-segmentation--rfm-analysis">⬆️ Back to top</a></p>
