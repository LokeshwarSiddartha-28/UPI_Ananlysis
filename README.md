# 📱 UPI Transaction Analysis Dashboard

**End-to-end analysis of 500K+ UPI transactions** — tracking transaction health, customer behavior, merchant & bank performance, fraud & risk exposure, and geographic trends using Power BI.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-Data%20Analysis%20Expressions-orange)

---

## 📌 Overview

UPI (Unified Payments Interface) processes millions of transactions daily across banks, merchants, and payment apps. This project simulates a real-world fintech analytics function — turning **502,887 raw transaction records** into a decision-ready Power BI report covering transaction performance, customer segmentation, fraud detection, and regional trends.

The goal: build the kind of dashboard a UPI operations or risk team would actually use every week to answer *"what changed, and where's the fire?"*

---

## 🎯 Business Objective

| Stakeholder | Question the dashboard answers |
|---|---|
| Operations | Are transactions succeeding? Why are they failing? |
| Risk & Fraud | Where is fraud concentrated — which states, banks, merchants, payment modes? |
| Growth / Marketing | Which customer segments and geographies drive the most value? |
| Finance | What's the cashback outflow, and where's the highest-value merchant activity? |

---

## 🗃️ Dataset

- **502,887 transaction-level records**, 22 raw fields
- Fields include: `Transaction_ID`, `Transaction_Date`, `Transaction_Time`, `UPI_App`, `Customer_ID`, `Age_Group`, `Gender`, `State`, `City`, `Merchant_Name`, `Merchant_Category`, `Transaction_Type`, `Payment_Mode`, `Bank_Name`, `Amount_INR`, `Cashback_INR`, `Transaction_Fee_INR`, `Status`, `Failure_Reason`, `Device_OS`, `Risk_Score`, `Is_Suspected_Fraud`
- Time period covered: **May 2026**

---

## 🛠️ Tools & Tech Stack

| Tool | Purpose |
|---|---|
| **MySQL** | Storing raw data at scale, cleaning (nulls, duplicates, data types), deriving KPI logic via SQL before visualization |
| **Excel** | Quick pivot-based validation of SQL output, sanity-checking KPI numbers |
| **Power BI** | Data modeling (star schema), DAX measures, interactive report build, final delivery layer |
| **DAX** | Success/failure rate, fraud %, risk scoring aggregates, customer/merchant/bank-level KPIs |

---

## 🏗️ Data Model

Built as a **star schema** rather than a single flat table — one fact table connected to five dimension tables, with a dedicated measures table for all DAX logic:

```
                     Dim_Date
                        │
   Dim_Customer ─────┐  │  ┌───── Dim_Location
                      │  │  │
                    ┌─▼──▼──▼─┐
                    │  data   │  (fact table — 502,887 rows)
                    └─▲──▲──▲─┘
                      │  │  │
      Dim_UPI ────────┘  │  └──── Dim_Bank
                          │
                    Dim_Merchant

              All Measures (centralized DAX layer)
```

**Why this matters:** centralizing every KPI as a DAX measure (rather than scattering calculated columns across the fact table) means every number recalculates correctly no matter how the report is sliced — by state, bank, merchant, app, or date range.

---

## 📊 Dashboard Pages

### 1️⃣ Executive Summary

![Executive Summary](<Executive Report.png>)

High-level pulse of the business — total transactions, revenue, success/failure rate, fraud %, cashback outflow, and daily trends.

**Key KPIs:** 502.887K transactions · ₹442.48M total value · 91% success rate · 7% failure rate · 3.4% fraud rate · ₹3.46M total cashback · 387K customers · ₹879.88 average transaction value

Includes daily transaction/revenue trends, transaction status split, payment mode breakdown, and UPI app-wise transaction value.

### 2️⃣ Customer Analytics

![Customer Analytics](<Customer Report.png>)

Segments the customer base by age, gender, and geography, and surfaces top spenders.

- 25–34 age group dominates transaction volume (172K+ unique customers)
- Gender split: 53% male, 45% female, 1% other
- 1.30 average transactions per customer · ₹1,119 average spend per customer

### 3️⃣ Merchant & Bank Analytics

![Merchant and Bank Analytics](<Merchant and Bank Report.png>)

Ranks merchants and banks by successful spend and success rate, to identify where value concentrates and where reliability drops.

- Top merchant: **HP Petrol Pump** · Top bank: **HDFC Bank**
- ₹402.89M in total successful spend across 457.63K successful transactions
- Bank success rates cluster tightly between 90.86%–91.19% — no major outlier bank

### 4️⃣ Fraud & Risk

![Fraud and Risk](<Fraud and Risk Report.png>)

The highest-stakes page — fraud trend over time, fraud/risk exposure by bank and merchant, failure reason breakdown, and hourly risk pattern.

- 17.1K suspected fraud transactions (3.4% fraud rate), ₹15.55M in fraud value
- Average risk score: 50.38 across the base
- Fraud concentrates in **UPI ID** and **QR Scan** payment modes (54K and 53K high-risk transactions respectively)
- Top failure reasons: insufficient balance, beneficiary bank issues, transaction timeout

### 5️⃣ Geographic Analysis

![Geographic Analysis](<Geographic Report.png>)

State and city-level view of transaction volume, value, success/failure rates, and fraud/risk exposure, plus a filled map of fraud rate by state.

- Delhi, Maharashtra, and Karnataka lead in transaction volume and value
- Howrah, Warangal, and Kolkata top the list for suspected fraud by city

### 6️⃣ Quick Insights

![Quick Insights](<Quick Report.png>)

A narrative summary page — the one page built for someone who won't dig through the other five. Translates the numbers into plain-language business takeaways.

**Sample insights surfaced:**
- Top 5 states contribute 56% of total transaction value; Maharashtra leads in both volume and value
- High-risk transactions (30.9%) are meaningfully higher than confirmed suspected fraud (3.4%) — only 10.3% of high-risk transactions turn out to be actual fraud
- Insufficient balance and bank declines account for 56.5% of all failures — an operational, not a fraud, problem
- Evening hours see peak transaction activity, making that window the priority for real-time fraud monitoring
- UPI ID and QR Scan together account for 59.8% of high-risk transactions

---

## 🚀 Workflow

1. **Ingest** raw transaction data into MySQL
2. **Clean & validate** — handle nulls/duplicates, correct data types, standardize categorical fields
3. **Derive KPI logic in SQL** — success/failure rate, fraud rate, top merchants/categories — validated against Excel pivots
4. **Model in Power BI** — star schema (fact + dimensions), centralized measures table
5. **Build DAX measures** — rates, ratios, and aggregates that respond correctly across all filter contexts
6. **Design report pages** — Executive Summary → Customer → Merchant & Bank → Fraud & Risk → Geographic → Quick Insights
7. **Translate to insights** — narrative takeaways tied to specific numbers, not just charts

---

## 📂 Repository Structure

```
UPI-Transaction-Analysis/
│
├── UPI_Analysis.zip            # Power BI report file (zipped — GitHub file size limit)
├── phonepay_raw_data.zip       # Raw source dataset (zipped — 502,887 rows)
├── README.md                   # This file
├── Executive Report.png
├── Customer Report.png
├── Merchant and Bank Report.png
├── Fraud and Risk Report.png
├── Geographic Report.png
└── Quick Report.png
```

> **Note:** the `.pbix` and raw dataset are zipped due to GitHub's file size limits. Download and extract `UPI_Analysis.zip` to open the report in Power BI Desktop.

---

## 🔭 Future Enhancements

- Add **Device_OS** (Android vs iOS) behavioral breakdown
- Break out **Transaction_Type** (P2P / P2M / Bill Payment / Recharge) as its own dimension view
- Add **Transaction_Fee_INR** as a margin/financial KPI alongside cashback
- Migrate the MySQL layer to a live/scheduled connection for near-real-time refresh

---

## 🙋 Author

**Lokeshwar Siddartha**
Programmer Analyst | BI & Data Analytics
📍 Andhra Pradesh, India

*Feedback and suggestions are welcome — feel free to open an issue or connect.*
