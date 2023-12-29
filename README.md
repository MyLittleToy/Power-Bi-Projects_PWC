  # PWC SWITZERLAND - Task 2

  **Dataset:**
[01 Call-Center-Dataset.xlsx](https://github.com/MyLittleToy/Power-BI-Projects/files/12642988/01.Call-Center-Dataset.xlsx)

**Project Goals:**
Create a dashboard in Power BI for Claire that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset. Get creative! 

KPIs include:
- Overall customer satisfaction
- Overall calls answered/abandoned
- Calls by time
- Average speed of answer
- Agent’s performance quadrant -> average handle time (talk duration) vs calls answered
![image](https://github.com/MyLittleToy/Power-BI-Projects/assets/139712656/04c153b1-f9b8-46a5-83db-862c6ff140a1)



  # PWC SWITZERLAND - Task 3

**Dataset:**
(https://github.com/MyLittleToy/Power-BI-Projects/files/12642963/02.Churn-Dataset.xlsx)



**Project Overview:**
A few weeks after presenting your dashboard to the management, the Retention Manager from the telecom reaches out to you directly. He was impressed by your work and asked if you can put together a dashboard about customer retention.

In addition, to better understand the data, the telecom Retention Manager has scheduled a meeting with the engagement partner at PwC to cover these points:

Customers in the telecom industry are hard-earned: we don’t want to lose them
The retention department is here to get customers back in case of termination 
Currently, we get in touch after they have terminated the contract, but this is reactionary: it would be better to know in advance who is at risk.
We  have done customer analysis with Excel; it has always ended in a dead-end
We would like to know more about our customers: visualised clearly so that it’s self-explanatory for our management
The Retentions Manager has provided some information, see below link.

[02 Churn[PhoneNow inputs (3).pdf](https://github.com/MyLittleToy/Power-BI-Projects/files/12642964/PhoneNow.inputs.3.pdf)

**Project Goals:**
- Customers who left within the last month
- Services each customer has signed up for phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- Customer account information: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges and number of tickets opened in the       categories administrative and technical
- Demographic info about customers – gender, age range, and if they have partners and dependents


**Data Cleanup Phase:**
I utilised Power Query to conduct the following tasks:
- Data type validation
- Checking for 'nulls' within the data set.
  - Within the dataset I identified 11 records in the 'TotalCharges' column that had null values.  I created a custom column to replace the null values with the values from the monthly charges column with the assumption that these 11 customers were new customers and did not have any other monthly charges.
    = Table.AddColumn(#"Replaced Value1", "Custom", each if [TotalCharges] = null then [MonthlyCharges] else [TotalCharges])

Changed data type from whole number to text and replaced values in the 'Senior Citizen' column from (0,1) to (Yes/No)

**Other measures that I utilised when analysing the dataset were:**
#ChurnRate = COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes")) / COUNTROWS('01 Churn-Dataset')

#AvgTenureChurned = AVERAGEX(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"), '01 Churn-Dataset'[Churn])

#ChurnRatePaymentMethod = DIVIDE(CALCULATE(COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"))),CALCULATE(COUNTROWS('01 Churn-Dataset')),0)

#AvgMonthlyChargesChurned = AVERAGEX(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"), '01 Churn-Dataset'[Churn])

#AdminTicketResolutionRate = DIVIDE(SUM('01 Churn-Dataset'[numAdminTickets]), COUNTROWS('01 Churn-Dataset'))

#ChurnRateM2M = DIVIDE(CALCULATE(COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes" && '01 Churn-Dataset'[Contract] = "Month-to-Month"))), CALCULATE(COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Contract] = "Month-to-Month"))))

#CountDevicePro = CALCULATE (COUNTA ('01 Churn-Dataset'[DeviceProtection]), '01 Churn-Dataset'[DeviceProtection] = "Yes" )


  # PWC SWITZERLAND - Task 4

**Project Overview:**
Human Resources at our telecom client is highly into diversity and inclusion. They’ve been working hard to improve gender balance at the executive management level, but they’re not seeing any progress. They’re reaching out to us for help.

At PwC Switzerland we are often approached by clients seeking support with diversity and inclusion. Companies need a workforce of diverse talents and backgrounds to succeed in an increasingly complex and heterogeneous world. To us, diversity and inclusion are business imperatives, not just nice-to-haves. We aim for all of our teams to feel welcome and appreciated. But actually achieving this and unlocking its potential involves a whole set of practical challenges.

This is particularly important as PWC Switzerland often provide support to clients on how to enhance their employee's experience by:

Making an organisation more inclusive and diverse;
Attracting more women to their organisation;
Retaining & developing diverse talent;
Identifying and mitigating systemic bias (for example gender bias or sexual discrimination) in their policies and practices;
Ensuring the employee lifecycle is fair and robust from application to exit;
Measuring and applying fair pay practices.

**Project Goals:**
- Define relevant KPIs in hiring, promotion, performance and turnover, and create a visualisation
- Write what you think some of the root causes of their slow progress in improving gender balance at the executive management level might be

**Data Cleanup Phase:**
I utilised Power Query to conduct the following tasks:

- Data type validation
- Checking for 'nulls' within the data set. replaced leaver year nulls with 'current', replaced job role after promotion nulls with 'no promotion'
- replaced FTE group non full timers as part time.
- replaced time in job level before promotion nulls to n/a
- replaced fy19 perf rating nulls to 0 to reflect none yet undertaken
- ABIVE ON PHARMA GROUP TABLE
- 
- Removal of columns that would not be used for my analysis


**Visual Creation Phase:**

  Key Performance Indicators
  1. Number of employees, leavers and hires by gender
  2. Percentage of promotions by gender and year (FY20 & FY21)
  3. Age distribution
  4. Gender distribution
  5. Nationality distribution
  6. Job-level distribution
  7. Time-type distribution
  8. Average Performance of gender, leavers
  9. Performance Rate distribution
  10. Average Performance Rate by Positions, Age, Region
  11. Comparison performance between leaver and non-leaver by department
  12. Indicators of the gender balance of new hire FY20, Promotion FY21, Turnover rate
  13. Executive gender balance
  14. Average Time at the Job level
  15. Hiring trend and hiring distribution by nationality
  16. Promotion and Turnover rate FY 21





