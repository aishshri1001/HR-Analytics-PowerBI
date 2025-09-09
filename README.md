# HR-Analytics-PowerBI
Power BI HR analytics report with 10 key workforce insights (headcount, gender breakdown, age distribution, salary analysis, etc.)

# Overview

This project simulates a real-world HR analytics engagement for a chocolate manufacturing company. I built a repeatable pipeline and an interactive dashboard to help leadership answer:

How many employees are in each job role, and what is the gender distribution?

How is the age and experience of staff distributed across departments?

Which jobs pay more, and who are the top earners?

How does educational qualification correlate with salary?

How has staff grown over time, and how is leave balance managed?

# Stack

Power BI Desktop (reporting & visualization)

Power Query (M) (data cleaning & transformation)

DAX (measures for headcount, cumulative totals, leave balance, salary analysis)

# Project Planning — AIMS Grid

Purpose: Provide a single view of HR metrics, reduce manual Excel reporting, and enable data-driven workforce decisions.

Stakeholders: HR Director, Department Heads, Operations Managers.

End Result: An interactive Power BI dashboard with drill-downs by department, job title, gender, age, and leave balance.

Success Criteria:

Accurate headcount, salary, and leave KPIs

Ability to identify top/bottom earners per job

Quick insights into staff growth trends and qualification impact on salary

# Data Sources

Dataset: Sample HR data in Excel (HR_Data.xlsx)

Fields: Employee ID, Name, Gender, Age, Job Title, Salary, Date of Joining, Educational Qualification, Leave Balance

Record Volume: ~161 employees

Note: You can replicate the dashboard using any HR dataset with similar fields.

# Data Cleaning & Transformation (Power Query)

Key steps performed in Power Query:

Imported data from Excel → Used Transform Data to clean and structure the dataset.

Set headers correctly → Used Use First Row as Headers to fix column names (previously Column1, Column2…).

Type conversion → Converted Date of Joining to Date type; numeric fields (Salary, Age, Leave Balance) to number type.

Renamed table → Renamed the main table as Staff for easier reference in Power BI.

Age binning → Created age bins of 5 years each for meaningful age distribution analysis.

First letter extraction → Added a column for the first letter of employee names to enable filtering by initials in the dashboard.

# Dashboard Highlights

Headcount by Job Title → Bar chart showing number of employees per role.

Gender Breakdown → Pie chart & slicers for job-specific breakdown.

Age Distribution → Column chart with age bins, stack or clustered by gender.

Salary Analysis → Average, min, max salary per job; top/bottom earners per role.

Qualification vs Salary → Column chart showing average salary by education level.

Staff Growth Trend → Cumulative headcount over time.

Employee Filtering → Filter staff by first letter of their name.

Leave Balance Analysis → Average leave per job & count of employees with >20 days leave.

Final Dashboard → Consolidated page with KPIs, charts, and slicers.

Interactive Features: Slicers for job title, gender, age, and name initials. Hover tooltips for detailed insights.

# Example Calculations (DAX Measures)

Avg. Salary = AVERAGE(staff[Salary])

Avg. Leave Balance = AVERAGE(staff[Leave Balance])

Cumulative Headcount =
VAR currentDate = LASTDATE(staff[Date of Join]) RETURN CALCULATE([Headcount], ALL(staff[Date of Join]), staff[Date of Join] <= currentDate)

Headcount = COUNTROWS(staff)

Leave Balance over 20 days = CALCULATE([Headcount], staff[Leave Balance] > 20)

Max Salary = MAX(staff[Salary])

Min Salary = MIN(staff[Salary])
