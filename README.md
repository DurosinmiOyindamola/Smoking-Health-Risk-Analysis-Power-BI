# Smoking-Health-Risk-Analysis-Power-BI
Power BI dashboard analyzing smoking behavior and health risk patterns across 2,500+ patient records.
## Table Of Content
- [Project Overview](#projectoverview)
- [Objectives](#objectives)
- [Data Description](#datadescription)
- [Data Modeling](#datamodeling)
- [Process](#process)
- [Tools Used](#toolsused)
- [Key Measures & Calculations](#keymeasures&calculations)
- [Key Insights](#keyinsights)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)
### Project Overview
This project analyzes the impact of smoking behavior on health outcomes using an interactive Power BI dashboard. The analysis is based on a dataset of over 2,500 patient records, focusing on how smoking status, age, and BMI influence key health risks.
The goal is to transform raw healthcare data into actionable insights that support early intervention and preventive healthcare decision-making.
### Objectives
#### The main objectives of this analysis are to:
- Analyze the relationship between smoking behavior and health outcomes
- Identify high-risk groups based on age, BMI, and smoking patterns
- Evaluate cholesterol and hypertension risk levels across demographics
- Examine organ health outcomes (Heart, Kidney, Liver, Lungs)
- Build an interactive dashboard for clear and intuitive data exploration
### Data Description
#### This project uses three related datasets:
##### 1. Healthcare Dataset (Main Table)
###### Contains patient-level information:
- Patient ID
- Age and gender
- Age Group
- Smoking status (Never, Current, Former)
- BP_Risk
- Cigarettes_per_day
- Family History Risk
- BMI
- Cholesterol Level
- Alcohol Consumption
- Organ and Organ Condition
- Years of Smoking
- Avg.BMI & Avg.AGE
##### 2. Condition & Organ Dataset
- Organ type (Heart, Kidney, Liver, Lungs, Human Body)
- Health status (Healthy / Damaged)
##### 3. Image Dataset
- Image-related identifiers linked to patient records
- Used for visual representation within the dashboard
### Data Modeling
#### The datasets were combined in Power BI using one to many relationships:
The Healthcare dataset serves as the central table
Other datasets were connected using a common key 
Relationships were structured to allow cross-filtering and interaction
<img width="1328" height="717" alt="health data model" src="https://github.com/user-attachments/assets/304e9ba0-df8a-408e-b9aa-6563b29234d4" />
This approach improves analysis by enabling multi-dimensional insights across datasets.
### Process
#### Data Cleaning & Preparation
- Handled missing values and inconsistencies
- Standardized categorical variables
- Ensured correct data types
#### Data Analysis
- Explored smoking patterns across age and gender
- Analyzed health risks across different groups
- Evaluated combined effects of smoking, age, and BMI
#### Dashboard Development
 -Built an interactive dashboard in Power BI
- Added organ conditions to filter the damaged and healthy organs
- Designed visuals for clear comparison and storytelling
<img width="1021" height="625" alt="Damaged  Human" src="https://github.com/user-attachments/assets/08593e7b-dcd3-4eb3-b1bd-4ed3c201d7d5" />

### Key Measures & Calculations
#### Average Age Comparison
vs Avg Age = 
VAR _CurrentAge = AVERAGE(health_dataset[Age])
VAR _OverallAge = CALCULATE(AVERAGE(health_dataset[Age]), ALL(health_dataset))
VAR _Diff = _CurrentAge - _OverallAge

RETURN
SWITCH(
    TRUE(),
    _Diff > 0, UNICHAR(9650) & " " & FORMAT(_CurrentAge, "0.0"),
    _Diff < 0, UNICHAR(9660) & " " & FORMAT(_CurrentAge, "0.0"),
    FORMAT(_CurrentAge, "0.0")
)
#### Average BMI Comparison
vs Avg BMI = 
VAR _CurrentBMI = AVERAGE(health_dataset[BMI])
VAR _OverallBMI = CALCULATE(AVERAGE(health_dataset[BMI]), ALL(health_dataset))
VAR _Diff = _CurrentBMI - _OverallBMI

RETURN
SWITCH(
    TRUE(),
    _Diff > 0, UNICHAR(9650) & " " & FORMAT(_CurrentBMI, "0.0"),
    _Diff < 0, UNICHAR(9660) & " " & FORMAT(_CurrentBMI, "0.0"),
    FORMAT(_CurrentBMI, "0.0")
)
#### Age Group Column
Age Group = 
SWITCH(
    TRUE(),
    health_dataset[Age] <= 28, "18–28",
    health_dataset[Age] <= 38, "29–38",
    health_dataset[Age] <= 48, "39–48",
    health_dataset[Age] <= 58, "49–58",
    health_dataset[Age] <= 68, "59–68",
    "69+"
)
### Key Insights
- Active smokers are increasingly in high-risk health categories
- The 29–38 age group shows elevated cholesterol and hypertension risk
- Health outcomes are influenced by age, BMI, and smoking combined
- Non-smokers show lower risk, but age and BMI still matter
- Prevention should be holistic, not smoking-focused alone
### Recommendations
- Focus on early intervention for ages 29–38
- Promote smoking cessation programs
- Encourage healthy lifestyle habits (BMI management, diet, exercise)
- Increase routine health screenings
- Use data-driven monitoring for better health decisions
### Conclusion
This project demonstrates how data analytics can be used to uncover meaningful health insights. By combining data modeling, analysis, and visualization, it highlights the importance of early intervention and preventive healthcare strategies.
