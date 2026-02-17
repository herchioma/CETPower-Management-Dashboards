# CETPower Management Dashboard  
Finance, Production and Inventory Analytics Looker Studio Case Study

---

## Project Overview

Dashboard for CETPower, a power generation and energy distribution company operating across multiple Nigerian sites.

The dashboard was designed to:

- Provide real-time financial visibility  
- Monitor energy production performance  
- Track operational efficiency across sites  
- Support management-level decision-making  

The solution includes:

- A structured dataset (`CETPower_Sample_Data.xlsx`)  
- A fully designed dashboard mockup (`CETPower_Looker_Studio_Mockup.html`)  
- Clear business logic, KPIs, and data modeling structure  

---

# Business Problem

CETPower leadership needs a centralized reporting system to answer the following:

## Finance

- What is our total cash position across all banks?  
- Are revenues growing month over month?  
- Are expenses increasing faster than revenue?  
- What categories are driving the highest cost?  
- What is our net cash flow and margin trend?  

## Production

- How much kWh are we generating monthly?  
- Which site performs best?  
- Which sites are underutilized?  
- Are we meeting production targets?  
- How does performance trend over time?  

## Inventory

- What equipment requires maintenance?  
- Where are stock risks emerging?  
- What assets are underperforming?  

---

# Analytical Questions Solved

## Finance Dashboard

1. What is the total current cash position?  
2. What is Month to Date Revenue?  
3. What is Month to Date Expense?  
4. What is Net Cash Flow?  
5. What is the revenue versus expense trend over the last 12 months?  
6. What categories contribute most to expenses?  
7. What are balances per bank account?  
8. What are the most recent transactions?  

---

## Production Dashboard

1. Total kWh generated Month to Date  
2. Year to Date production  
3. Fleet utilization rate  
4. Best performing site  
5. Sites below target  
6. Production trend over last six months  
7. Site comparison performance  

---

# Project Structure

```
CETPower-Dashboard/
│
├── CETPower_Looker_Studio_Mockup.html
├── CETPower_Sample_Data.xlsx
├── README.md
└── assets/ (optional screenshots)
```

---

# Data Dictionary

Below is the logical data model based on the Excel dataset.

## 1. Finance_Transactions Table

| Column Name   | Data Type | Description                                      |
|---------------|-----------|--------------------------------------------------|
| Date          | Date      | Transaction date                                 |
| Type          | Text      | Revenue or Expense                               |
| Category      | Text      | Fuel, Salaries, Energy Sales and others          |
| Amount        | Numeric   | Transaction value in Naira                       |
| Bank_Account  | Text      | GTB, Zenith, Access, UBA                         |

### Business Logic

- Revenue equals positive amount  
- Expense equals negative amount  
- Net Cash Flow equals sum of revenue minus sum of expense  

---

## 2. Bank_Balances Table

| Column Name      | Data Type | Description                   |
|------------------|-----------|-------------------------------|
| Bank_Account     | Text      | Account name                  |
| Current_Balance  | Numeric   | Current available balance     |

### KPI

Total Cash Position equals sum of current balance  

---

## 3. Production_Data Table

| Column Name       | Data Type  | Description                  |
|-------------------|------------|------------------------------|
| Date              | Date       | Production date              |
| Site              | Text       | Location of facility         |
| kWh_Generated     | Numeric    | Energy generated             |
| Target_kWh        | Numeric    | Expected output              |
| Utilization_Rate  | Percentage | Efficiency rate              |
| Weather           | Text       | Clear, Rainy or Cloudy       |

### KPI Calculations

- Fleet Utilization equals average utilization rate  
- Best Site equals maximum utilization rate  
- Below Target equals count of sites where utilization is below threshold  

---

# Dashboard Design Structure

## Page 1: Finance Overview

### KPI Scorecards

- Total Cash Position  
- Month to Date Revenue  
- Month to Date Expenses  
- Net Cash Flow  

### Visualizations

- Time Series Line Chart showing Revenue versus Expenses  
- Donut Chart showing Expense Breakdown  
- Bar Chart showing Bank Balances  
- Transaction Table  

### Filters

- Period  
- Transaction Type  
- Category  
- Bank  

---

## Page 2: Production Overview

### KPI Scorecards

- Total kWh Month to Date  
- Year to Date Production  
- Fleet Utilization  
- Best Site  
- Sites Below Target  

### Visualizations

- Stacked Column Chart showing kWh by Site over six months  
- Site Performance Comparison Table  
- Utilization Progress Bars  

### Filters

- Period  
- Site  
- Weather  

---

# Key Metrics and Formulas

```
Total Cash Position = SUM(Current_Balance)

Month to Date Revenue = SUM(Amount WHERE Type = "Revenue")

Month to Date Expense = SUM(Amount WHERE Type = "Expense")

Net Cash Flow = Revenue - Expense

Profit Margin = Net Cash Flow / Revenue

Fleet Utilization = AVG(Utilization_Rate)

Year to Date Production = SUM(kWh_Generated)
```

---

# Data Modeling Approach

- Star schema design  
- Fact tables:
  - Finance_Transactions  
  - Production_Data  
- Dimension tables:
  - Bank_Accounts  
  - Sites  
  - Categories  
  - Date  

The model is optimized for aggregation, filtering and performance in BI tools.

---

# Design Principles Used

- Executive first layout  
- KPI driven storytelling  
- Minimal cognitive load  
- Color coded performance indicators  
- Progressive disclosure from KPIs to trends to detail tables  
- Decision oriented labeling  

---

# Future Improvements

- Real time API integration  
- Predictive revenue forecasting  
- Anomaly detection for expenses  
- Maintenance prediction model  
- Automated alert system  
