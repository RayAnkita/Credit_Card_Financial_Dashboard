# Credit_Card_Financial_Dashboard
Power BI Dashboard
Project Objective: To develop a comprehensive credit card dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

# Steps: 
Load the Data set into the Power BI Desktop application.
Understand the data and based on understanding add more columns for better analysis.

# Dax Queries: 
1- AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)

2- IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)

3- week_num2 = WEEKNUM('public cc_detail'[week_start_date])

4- Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

5- Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

6- Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

# Insights:
• Overall revenue is 55M
• Total interest is 7.8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 30M, female 25M
• Blue & Silver credit card are contributing to over a 90% of overall transactions
• TX, NY & CA is contributing to over 65%
• Overall Activation rate is approximately 55.5%
• Overall Delinquent rate is approximately 6.06%
