# Data Dictionary — Indian Banking Transaction Analytics

Describes the tables and fields used in the Power BI data model. Raw data is not included in this repo (synthetic/sample data only recommended for public sharing).

## Table: `indian_banking_transactions` (fact table)

| Column | Type | Description |
|---|---|---|
| transaction_id | Text/ID | Unique identifier for each transaction |
| transaction_date | Date | Date the transaction occurred (links to Date_calendar) |
| customer_id | Text/ID | Unique identifier for the customer |
| account_type | Text | Type of bank account: Savings, Current, Salary, NRI, Fixed Deposit |
| transaction_type | Text | Transfer/payment rail used: UPI, IMPS, NEFT, RTGS, Cheque, Credit Card, Net Banking, ATM Withdrawal, POS, Auto Debit |
| channel | Text | Channel through which the transaction was initiated: Mobile App, Web, ATM, POS Terminal, Branch, API |
| transaction_amount | Decimal | Value of the transaction (₹) |
| transaction_status | Text | Outcome of the transaction: Success, Failed |
| is_fraud | Boolean/Flag | Whether the transaction was flagged as fraudulent (1/0) |
| merchant_category | Text | Category of merchant involved: Retail, E-Commerce, Food & Dining, Salary, Travel, etc. |
| state | Text | State associated with the customer/transaction, used for the map visual |

## Table: `Date_calendar` (dimension)

| Column | Type | Description |
|---|---|---|
| Date | Date | Calendar date (one row per day) |
| Year | Integer | Calendar year |
| Month | Text/Integer | Month name/number |
| MonthYear | Text | Combined month-year label used for trend charts |

## Table: `Fraud Funnel` (dimension / measure table)

| Field | Type | Description |
|---|---|---|
| Active Customers | Measure | Count of customers with at least one transaction |
| Customers with Fraud | Measure | Count of customers with at least one fraud-flagged transaction |
| Repeat Fraud (+2) | Measure | Count of customers with 2 or more fraud-flagged transactions |
| Frequent Fraud (3x) | Measure | Count of customers with 3 or more fraud-flagged transactions |

## Key DAX Measures (examples)

| Measure | Description |
|---|---|
| Total Transaction | Count of all transactions |
| Total Value | Sum of transaction_amount |
| Failure Rate | Failed transactions ÷ Total transactions |
| Fraud Rate | Fraud-flagged transactions ÷ Total transactions |
| Avg Transaction Value | Average transaction_amount across all transactions |
| Avg Fraud Value | Average transaction_amount among fraud-flagged transactions |
