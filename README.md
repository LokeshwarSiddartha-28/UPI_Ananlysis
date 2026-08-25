UPI Transaction Analysis — Power BI

Overview

This project analyzes UPI transaction data to understand transaction activity, customer behavior, merchant and bank performance, geographic patterns, and fraud-related risk.

The project was built as an end-to-end Power BI analysis, starting from transaction-level data and turning it into KPIs, trends, comparisons, and business insights.

Business Objective

The analysis focuses on answering practical business questions:

How many UPI transactions are happening?

What is the total transaction value?

What is the success and failure rate?

Which customers and customer segments contribute to activity?

Which merchants and banks have the highest transaction value?

Which states and cities have the highest transaction activity?

Where is suspected fraud concentrated?

Which transactions fall into the high-risk segment?

Which payment modes show higher risk?

When during the day is transaction activity highest?

What operational issues are contributing to failed transactions?

Dashboard Pages

1. Executive Summary

Provides the overall view of UPI activity.

Key metrics and analysis:

Total Transactions — 502.887K

Total Transaction Value — ₹442.48M

Success Rate — 91%

Failure Rate — 7%

Total Cashback — ₹3.46M

Fraud Rate — 3.4%

Total Customers — 387K

Average Transaction Amount — ₹879.88

Daily transaction trend

Daily transaction value trend

Transaction status

Payment mode

UPI app-wise transaction value

2. Customer Analytics

Focuses on customer distribution and spending behavior.

Analysis includes:

Total customers

Average spend by customer

Transactions per customer

Customers by age group

Customer distribution by state

Customers by gender

Top 10 customers by successful spend

The dashboard shows that the 25–34 age group has the largest customer population in the dataset.

3. Merchant & Bank Analytics

Compares successful transaction performance across merchants, categories, and banks.

Analysis includes:

Total successful transaction value

Average transaction amount

Successful transactions

Top merchant by successful transaction value

Top 10 merchants

Successful transaction value by merchant category

Successful transaction value by bank

Bank success rate

Merchant success rate

The dashboard identifies HP Petrol Pump as the top merchant by successful transaction value and HDFC Bank as the top bank in the selected analysis.

4. Fraud & Risk

Examines suspected fraud, risk, and transaction failures.

Key metrics:

Suspected Fraud Transactions — 17.1K

Fraud Rate — 3.4%

Fraud Amount — ₹15.55M

Average Risk Score — 50.38

Failed Transactions — 35.2K

Failure Rate — 7%

Analysis includes:

Fraud trend over time

High-risk transactions by payment mode

Failure reasons

Fraud exposure by bank

Fraud exposure by merchant

Risk and suspected fraud by hour

Note: Is_Suspected_Fraud = Yes represents suspected fraud in the dataset. It is not treated as confirmed fraud.

5. Geographic Analysis

Examines transaction activity, value, failures, fraud, and risk across locations.

Analysis includes:

Top states by transaction volume

Top states by transaction value

State-wise successful transactions

State-wise failed transactions

States with highest fraud exposure

States with highest risk exposure

Top cities by transaction value

Top cities by suspected fraud

Fraud rate by state

6. Quick Insights

The final page converts the dashboard analysis into business-oriented findings.

It summarizes:

Transaction concentration

Fraud exposure

High-risk transactions versus suspected fraud

Operational failure issues

Top merchants

Peak transaction and risk periods

Payment mode risk

State-level transaction volume

State-level risk exposure

City-level suspected fraud

Major failure reasons

The analysis follows:

KPIs → Trends → Insights → Business Outcomes → Recommendations

Key Business Findings

Based on the dashboard analysis:

The dataset contains approximately 502.9K transactions with a total transaction value of approximately ₹442.48M.

The overall transaction success rate is 91%, while the failure rate is 7%.

The suspected fraud rate is 3.4%, representing approximately 17.1K suspected fraud transactions.

The 25–34 age group has the highest customer concentration.

Maharashtra is among the leading states for both transaction volume and transaction value.

A relatively small group of merchants contributes significantly to successful transaction value.

UPI ID and QR Scan together account for a large share of high-risk transactions.

Insufficient balance and bank-related decline/rejection reasons are major contributors to failed transactions.

Transaction activity is concentrated during the later part of the day, making peak periods relevant for transaction monitoring.

These findings should be interpreted in the context of the available dataset and filters.

Data Model

The Power BI model follows a fact-and-dimension structure.

Fact Table

data

The transaction table contains transaction-level information such as:

Transaction ID

Customer ID

Transaction date and time

Amount

Cashback

Bank

Merchant

Merchant category

Payment mode

UPI application

State and city

Transaction status

Risk score

Suspected fraud indicator

Failure reason

Dimension Tables

The model includes dimensions for:

Customer

Merchant

Bank

UPI

Location

Date

These dimensions are connected to the transaction fact table to support filtering and analysis.

Main Measures

The project uses DAX measures for the main KPIs and analytical calculations, including:

Total Transactions

Total Transaction Amount

Successful Transactions

Success Rate %

Failed Transactions

Failure Rate %

Total Cashback

Unique Customers

Average Transaction Amount

Average Spend by Customer

Transactions per Customer

Suspected Fraud Transactions

Fraud %

Fraud Amount

Average Risk Score

High-Risk Transactions

Bank Success Rate

Merchant Success Rate

Tools Used

Power BI — data modelling, DAX, visualizations, dashboard development and analysis

Power Query — data preparation and transformation

Excel / CSV — source data and initial data inspection

Analytical Approach

The project separates transaction volume from transaction value.

Transaction volume = number of transactions

Transaction value = total monetary value of transactions

This distinction is important when interpreting states, banks, merchants, and customer activity.

Similarly, suspected fraud is not treated as confirmed fraud.

For example, a state with a high number of suspected fraud transactions is not automatically considered the highest-risk state. Fraud rate, transaction volume, transaction value, and risk indicators need to be considered together.

Business Outcome

The dashboard provides a consolidated view of UPI activity and helps identify:

Major transaction markets

Customer segments

High-value merchants and banks

Operational failure areas

Fraud exposure

High-risk payment modes

Geographic risk concentration

Peak transaction periods

The purpose is to support decisions around transaction monitoring, operational improvement, and risk management rather than simply presenting charts.

Project Structure

UPI-Transaction-Analysis/
│
├── README.md
│
├── data/
│   └── raw_dataset.csv
│
├── powerbi/
│   └── UPI_Analysis.pbix
│
└── screenshots/
    ├── executive-summary.png
    ├── customer-analytics.png
    ├── merchant-bank-analytics.png
    ├── fraud-risk.png
    ├── geographic-analysis.png
    └── quick-insights.png

Dashboard Preview

Executive Summary



Customer Analytics



Merchant & Bank Analytics



Fraud & Risk



Geographic Analysis



Quick Insights



Project Status

Completed

The Power BI report covers the main transaction, customer, merchant, bank, geographic, fraud, risk, and time-based analysis required for this case study.
