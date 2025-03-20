# PWC Power BI Task 1 Call Center Trends
PWC Virtual Work Experience Programs Task 1
## Table of Contents :
-  Problem Statement
-  Datasource
-  Data Preparation
-  Data Modelling
-  Data Analysis (DAX)
-  Data Visualization Dashboard
-  Insights
## Problem Statement :
In this project, a dashboard was created in Microsoft Power BI for a call center manager to monitor various Key Performance Indicators (KPIs) essential for operational success. The dashboard provides insights into:
- Overall customer satisfaction.
- Call answer and abandonment rates.
- Distribution of calls over time.
- Average speed of answer.
- Trends in agent performance, specifically examining average handle time in comparison to the number of calls answered.
## Datasource :
The primary dataset used for this analysis, provided by Pwc, was the "01 Call-Center-Dataset" dataset. This dataset comprises:
Dataset Name: 01 Call-Center-Dataset
Observations: 10 columns, 5000 rows
## Data Preparation:
Data preparation was conducted in Power Query within Microsoft Power BI Desktop. The following steps were taken to prepare the data for analysis:
- Data Validation: Each column was checked to ensure it contained the correct data type.
## Data Modelling
Once the dataset was cleaned and validated, it was structured into a model suitable for analysis. The data model included:
- Date Table: Integrated for handling time intelligence calculations.
- Call Centre Trends Table: Main observational data used for KPI calculations.
- ![]
## Data Analysis (DAX)
Several DAX measures were created to derive insights from the data:
OverallCallsAnswered = CALCULATE(COUNTROWS('Call Centre'),ALL('Call Centre'[Answered (Y/N)]),'Call Centre'[Answered (Y/N)] = "Y")
OverallCallsAbandoned = CALCULATE(COUNTROWS('Call Centre'),'Call Centre'[Answered (Y/N)] = "N")
AvgTalkDurationSeconds = 
CALCULATE(
    SUMX('Call Centre', 
    HOUR('Call Centre'[AvgTalkDuration]) * 3600 + 
    MINUTE('Call Centre'[AvgTalkDuration]) * 60 + 
    SECOND('Call Centre'[AvgTalkDuration]))
    / COUNTROWS('Call Centre'),
    'Call Centre'[Answered (Y/N)] = "Y"
)
AvgCustomerSatisfaction = CALCULATE(AVERAGE('Call Centre'[Satisfaction rating]),'Call Centre'[Answered (Y/N)]="Y")
Abandoned Rate = DIVIDE([OverallCallsAbandoned],[CountofCalls])
Resolved Rate = DIVIDE([CallsResolved],[CountofCalls],0)
CountofCalls = COUNTROWS('Call Centre')
HourOfDay = HOUR('Call Centre'[Time])
## Data Visualization (Dashboard) :
