#  HR Analytics Dashboard - Power BI

##  Project Overview
This project is a dynamic **HR Analytics Dashboard** built in **Power BI**. It provides a comprehensive high-level view of the organization's workforce metrics, helping HR managers make data-driven decisions regarding employee retention, promotion eligibility, and retrenchment planning.

The dashboard transforms raw HR data into actionable insights using complex **DAX measures** and **Power Query** transformations.

## Key Features & KPIs
* **Employee Demographics:** Total employee count split by Gender (Male/Female) with percentage distributions.
* **Promotion Analysis:** Identifies employees due for promotion based on years since their last promotion (>= 10 years).
* **Retrenchment Planning:** Categorizes employees eligible for retrenchment based on long service tenure (>= 18 years).
* **Service Analysis:** Visualizes workforce distribution across different job levels and years of service.

##  Dataset
The dataset used for this project is the **HR Analytics Data** (often referred to as the IBM HR Analytics Employee Attrition & Performance dataset). It contains **1,470 rows** and **35 columns**.

### Key Columns Used:
| Category | Columns |
| :--- | :--- |
| **Demographics** | `Age`, `Gender`, `MaritalStatus`, `Education`, `EducationField` |
| **Job Info** | `Department`, `JobRole`, `JobLevel`, `BusinessTravel` |
| **Performance** | `PerformanceRating`, `JobSatisfaction`, `EnvironmentSatisfaction` |
| **Tenure & Promotion** | `YearsAtCompany`, `YearsInCurrentRole`, `YearsSinceLastPromotion`, `TotalWorkingYears` |
| **Employment Details** | `Attrition`, `OverTime`, `DistanceStatus` (Calculated), `Retrenchment Status` (Calculated) |

##  Visualizations Used
The dashboard employs a variety of custom-formatted visuals to present data clearly:

1.  **KPI Cards (Multi-Row & Single):**
    * **Total Employees:** Displays the headline headcount (1,470).
    * **Gender Split:** Separate cards for Male/Female counts and percentages using DAX measures.
    * **Due for Promotion:** A calculated card identifying employees stuck in the same role for 10+ years.
2.  **Stacked Column Charts:**
    * Used to analyze **Employee distribution by Job Role** and **Department**.
3.  **Donut/Pie Charts:**
    * Visualizes the proportion of employees by **Distance from Home** (Near, Far, Very Far).
4.  **Bar Charts:**
    * Displays **Job Satisfaction ratings** and **Job Level** breakdowns.
5.  **Slicers:**
    * Interactive filters for `Department`, `Job Role`, and `Gender` to allow users to drill down into specific segments.

## 🛠️ Data Transformation (Power Query)
The raw data was processed using Power Query Editor to ensure data quality:
1.  **Data Cleaning:** Split raw text data into 35 separate columns using Tab delimiters.
2.  **Conditional Columns:** Created custom columns for logic grouping:
    * `Promotion Status`: Logic based on `YearsSinceLastPromotion`.
    * `Retrenchment Status`: Logic based on `YearsAtCompany`.
    * `Distance Status`: Logic based on `DistanceFromHome`.
3.  **Data Types:** Validated and corrected data types for accurate calculation.

##  Key DAX Measures
Advanced DAX (Data Analysis Expressions) were used to create dynamic calculations:

```dax
/* Total Employees */
Total Emp = COUNTROWS('HR Analytics Data')

/* Gender Count */
Male = CALCULATE([Total Emp], 'HR Analytics Data'[Gender] = "Male")
Female = CALCULATE([Total Emp], 'HR Analytics Data'[Gender] = "Female")

/* Gender % */
% Male = DIVIDE([Male], [Total Emp], 0)
% Female = DIVIDE([Female], [Total Emp], 0)

/* Promotion Logic */
Due for Promotion = CALCULATE([Total Emp], 'HR Analytics Data'[Promotion Status] = "Due for promotion") + 0
