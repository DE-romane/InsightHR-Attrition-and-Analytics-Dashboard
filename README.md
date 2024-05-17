# InsightHR-Attrition-and-Analytics-Dashboard

a powerful HR analytics and attrition dashboard. This dashboard will enable you to analyze key HR KPIs such as Employee Count, Salary, Gender Ratio, and attrition patterns, helping you identify high-risk areas and uncover factors driving employee turnover. We will cover best practices for dashboard design, including selecting the right visualizations, filters, and metrics, and making the dashboard interactive, clear, and informative.

![HR Dashboard](https://github.com/DE-romane/InsightHR-Attrition-and-Analytics-Dashboard/assets/70475916/dfefa180-a68d-4707-ad7e-b0cd75c450be)

![Attrition Dashboard](https://github.com/DE-romane/InsightHR-Attrition-and-Analytics-Dashboard/assets/70475916/e94ecd5f-da0d-47fd-bf34-f521224d503e)



## Table of Contents
1. Objective and Business Requirement
2. Import and Explore the HR Data Set
3. Create a Data Model and Relationships
4. Define Key Performance Indicators (KPIs) and DAX Measures
5. Design the Dashboard Layout and Visualizations
6. Add Interactivity and Functionality
7. Drawing Insights from the Dashboard

## Objective and Business Requirement

### The Objective of the HR Dashboard
Before diving into the data, it’s crucial to align with your organization’s HR goals. Identify the specific questions your dashboard aims to answer. What insights are HR professionals seeking to understand employee attrition?

### Business Problem
- **Composition of the Workforce**: Analyze workforce composition by department, education field, business travel frequency, gender, job role, and age group.
- **HR KPIs**: Examine employee count, average salary, average monthly salary, average age, average salary hike, job satisfaction scores, and gender ratio.
- **Trends and Patterns**: Identify trends in employee data across different parameters like Education, Age group, and Department.
- **Attrition Analysis**: Identify factors influencing employee turnover and retention, such as salary, age, gender, education, and demographics. Gain insights into high attrition areas to inform targeted retention strategies.

## Import and Explore the HR Data Set

### Import the Data Set
The HR data set, a CSV file with information about 1470 employees (age, gender, department, job role, salary, education, performance, satisfaction, attrition, etc.), is available online. Follow these steps to import it into Power BI:
1. Open Power BI Desktop and click on `Get data`.
2. Select `Text/CSV` from the data sources list and locate the CSV file.
3. Click on `Load` to import the data.

### Explore the Data
Use the Data view and Model view in Power BI to examine the data, perform data cleaning, transformation, and validation using the Power Query Editor.

- **Data Examination**:
  - Check rows, columns, names, and data types.
  - Analyze numerical variables (range, mean, median, mode, standard deviation, distribution).
  - Analyze categorical variables (frequency, percentage, proportion).
  - Handle missing, invalid, or inconsistent values.
  - Identify and decide on outliers or anomalies.
  - Visualize correlations or relationships using charts or graphs.

## Create a Data Model and Relationships

### Data Model
In our case, we have a single table. However, if multiple tables were involved, create relationships based on common columns (e.g., department column for HR and department tables).

### Creating Relationships
1. Drag and drop the common column from one table to the matching column in the other table in the Relationships view.
2. Adjust relationship properties (granularity, cardinality, direction).
3. Save the relationship.

## Define Key Performance Indicators (KPIs) and DAX Measures

### Creating KPIs and DAX Measures
KPIs and DAX measures are created in the Modeling tab using the DAX language. They should be relevant, accurate, simple, and match business requirements.

- **Creating a KPI**: 
  - Select an existing measure and click on `New KPI`.
  - Specify the goal, status, trend, format, and style of the KPI.

- **Creating a DAX Measure**:
  - Click on `New Measure`, enter the name and formula in the formula bar.
  - Use DAX functions, operators, and column references for calculations.
  - Format the measure (data type, display units, decimal places, text formatting).

### Example DAX Measures for HR Dashboard:
```DAX
// Measure to Calculate Attrition Count
Attrition Count = CALCULATE([Employee Count], HR_Analytics[Attrition]="Yes")

// Measure to Calculate Attrition Rate
Attrition Rate = DIVIDE([Attrition Count], CALCULATE([Employee Count], ALL(HR_Analytics[Attrition])), 0)

// Measure for Attrition Target
Attrition Target = 0.2

// Measure to Calculate Average Age
Average Age = AVERAGE(HR_Analytics[Age])

// Measure to Calculate Average Job Satisfaction
Average Job Satisfaction = AVERAGE(HR_Analytics[JobSatisfaction])

// Measure to Calculate Average Monthly Salary
Average Salary = [Monthly Salary]/[Employee Count]

// Measure to Calculate Average Salary Hike
Average Salary Hike = AVERAGE(HR_Analytics[PercentSalaryHike])

// Measure to Calculate Average Years at Company
Average Years = AVERAGE(HR_Analytics[YearsAtCompany])

// Measure to Calculate Employee Count
Employee Count = DISTINCTCOUNT(HR_Analytics[EmpID])

// Measure to Calculate Gender Ratio
Gender Ratio = DIVIDE(
    CALCULATE([Employee Count], HR_Analytics[Gender] = "Female"),
    CALCULATE([Employee Count], HR_Analytics[Gender] = "Male"),
    0
)

// Measure to Calculate Monthly Salary
Monthly Salary = SUM(HR_Analytics[MonthlyIncome])
```

## Design the Dashboard Layout and Visualizations

### Dashboard Layout
Use the Report view and Visualizations pane to arrange and customize visual elements like titles, filters, charts, and tables. Ensure the layout is simple, clear, and informative.

- **Title**: Summarize the main topic and purpose, e.g., “HR Analytics Attrition Dashboard”.
- **Filters**: Allow filtering by department, education field, business travel, gender, job role, or age group.
- **Charts**: Visualize KPIs and measures like attrition count, attrition rate, monthly salary, average age.
- **Tables**: Display detailed data by categories like job role, employee count, attrition rate, average years in the company.

### Example Visuals:
- **KPI Cards**: Employee Count, Average Salary, Monthly Salary, Average Age, Salary Hike, Job Satisfaction, Gender Ratio.
- **Charts**: Employee Count by Education Field and Department, Monthly Salary by Department.
- **Tables**: Breakdown of KPIs by Job Role, Employee Count by Age Group.

## Add Interactivity and Functionality

### Adding Interactive Elements
Use the Visualizations pane and Fields pane to enhance user interaction and dashboard functionality.

- **Slicers**: Filter data by selecting values from a list.
- **Buttons**: Perform actions like navigating to another page, opening bookmarks, or resetting filters.
- **Bookmarks**: Save and navigate between different states of the dashboard.
- **Selections**: Highlight or filter data by clicking on visual elements.
- **Bookmark Navigation**: Navigate between different states of your dashboard using bookmarks.
- **Page Navigation**: Create multiple pages and link them to buttons or other visuals for navigation.

### Example Interactivity:
- Slicers for filtering by department, education field, business travel, gender, job role, or age group.
- Buttons and bookmarks to toggle between different visuals or reset filters.



## Drawing Insights from the Dashboard

### Key Insights
- **Attrition Rate**: 16%, higher than the industry average of 12%. Key reasons include low salaries, high workload, and lack of career growth opportunities.
- **Employee Diversity and Inclusion**: Significant gender gap in HR, with only 33% female representation. Dominance of Life Sciences & Medical in education fields.
- **Employee Count and Salary**: Total employee count of 1233, average salary of $6,879, and monthly total payroll of $8.5M.
- **Age Group Distribution**: Majority in the 26-35 (490) and 36-45 (425) age groups.
- **Job Roles**: Largest roles are Sales Executives (269) and Research Scientists (245).
- **Highest Salaries**: Drawn by Managers ($17,201) and Research Directors ($15,947).
- **Gender Ratio**: Skewed towards one gender at 68%.
- **Attrition Details**: Total attrition count of 237 with a rate of 16%. High attrition in Sales (21%), R&D (19%), and HR (14%). Highest attrition among Sales Representatives (40%), Laboratory Technicians (24%), and HR Specialists (23%).
- **Business Travel Impact**: Higher attrition (25%) for frequent travelers compared to those who rarely travel (8%).
- **Job Satisfaction**: Higher attrition (23%) among dissatisfied employees.


### Use Insights for Decision-Making
These insights can be leveraged for strategic HR decisions and action plans, such as improving employee satisfaction, addressing gender diversity, enhancing retention strategies, adjusting salary structures, and understanding demographic impacts on attrition.
