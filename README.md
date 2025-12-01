# HR-Power-BI-Analytics-Dashboard
Building a Power BI dashboard for HR analytics data.

# 📊 HR Analytics Dashboard - Power BI

## 📝 Project Overview
This project is a dynamic **HR Analytics Dashboard** built in Power BI. It provides a comprehensive high-level view of the organization's workforce metrics, helping HR managers make data-driven decisions regarding employee retention, promotion eligibility, and retrenchment planning.

The dashboard transforms raw HR data into actionable insights using complex DAX measures and Power Query transformations.

## 📸 Dashboard Preview

## 🚀 Key Features & KPIs
* Employee Demographics: Total employee count split by Gender (Male/Female) with percentage distributions.
* Promotion Analysis: Identifies employees due for promotion based on years since their last promotion (>= 10 years).
* Retrenchment Planning: Categorizes employees eligible for retrenchment based on long service tenure (>= 18 years).
* Commute Analysis: classifies employees by distance from home (Very Close, Close, Very Far).
* Job Level & Service Year Analysis: Visualizes workforce distribution across different job levels and years of service.
* Interactive Tooltips: Hovering over charts reveals detailed breakdowns by gender and promotion status.

## 🛠️ Data Transformation (Power Query)
The raw data was processed using Power Query Editor to ensure data quality:
1.  Data Cleaning: Split raw text data into 35 separate columns using Tab delimiters.
2.  **Conditional Columns:** Created custom columns for logic grouping:
    * `Promotion Status`: Logic based on `YearsSinceLastPromotion`.
    * `Retrenchment Status`: Logic based on `YearsAtCompany`.
    * `Distance Status`: Logic based on `DistanceFromHome`.
3.  Data Types: Validated and corrected data types for accurate calculation.

## 🧮 Key DAX Measures
Advanced DAX (Data Analysis Expressions) were used to create dynamic calculations:

dax
/* Total Employees */
Total Emp = COUNTROWS('HR Analytics Data')

/* Gender Count */
Male = CALCULATE([Total Emp], 'HR Analytics Data'[Gender] = "Male")
Female = CALCULATE([Total Emp], 'HR Analytics Data'[Gender] = "Female")

/* Gender % */
% Male = DIVIDE([Male], [Total Emp], 0)
% Female = DIVIDE([Female], [Total Emp], 0)

/* Promotion Logic */
Due for Promotion = CALCULATE([Total Emp], 'HR Analytics Data'[Promotion Status] = "Due for promotion")

Visualizations Used
*KPI Cards: For high-level metrics (Total Employees, % Gender, Due for Promotion).
*Stacked Column Charts: To analyze "Total Employees by Service Year".
*Bar Charts: To visualize "Total Employees by Job Level".
*Donut/Pie Charts: For "Distance from Home" analysis.
*Slicers/Filters: To filter data by Department, Job Role, or Gender.

Dataset
The dataset includes standard HR fields such as:
*Age, Gender, MaritalStatus
*JobRole, Department, JobLevel
*YearsAtCompany, YearsSinceLastPromotion
*MonthlyIncome, DistanceFromHome
