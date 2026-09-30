# Employee Data Analysis Using Pandas

## Overview

This project demonstrates practical data analysis using Python and Pandas on an employee dataset. The analysis covers data inspection, filtering, aggregation, sorting, date-based analysis, grouping, feature engineering, and employee classification.

The project focuses on building fundamental Pandas skills through a structured employee dataset containing information about departments, salaries, joining dates, cities, age, and gender.

## Dataset

The dataset contains **8 employee records** with the following columns:

| Column     | Description                    |
| ---------- | ------------------------------ |
| EmpID      | Employee identification number |
| Name       | Employee name                  |
| Department | Employee's department          |
| Age        | Employee age                   |
| Salary     | Employee salary                |
| JoinDate   | Employee joining date          |
| City       | Employee's city                |
| Gender     | Employee gender                |

### Data Quality

* Records: 8
* Columns: 8
* Missing values: 0
* JoinDate converted to Pandas datetime format

## Objectives

The project explores employee information using Pandas and answers questions such as:

* Which employees belong to the IT department?
* Which employees are older than 30?
* Which employees joined after 2020?
* Which employees are located in New York or Chicago?
* What is the average salary?
* What is the maximum salary in each department?
* How many employees are located in each city?
* What is the average age of female employees?
* Which employees have the highest salaries?
* What are the average salary and age values?
* Who is the youngest employee in each department?
* Who joined the company most recently?
* How many years of experience does each employee have?
* How can employees be classified based on age?

## Analysis Performed

### 1. Data Loading and Inspection

The Excel dataset is loaded using Pandas:

```python
df = pd.read_excel("pandas_new.xlsx")
```

Initial exploration includes:

* Viewing the first records
* Inspecting column names
* Checking data types
* Checking dataset dimensions
* Checking missing values

### 2. Filtering

The project uses conditional filtering to extract specific employee groups.

Examples include:

* Employees in the IT department
* Employees older than 30
* Employees who joined after 2020
* Employees from New York and Chicago
* Female employees

### 3. Salary Analysis

The project calculates the overall average salary and the maximum salary within each department.

The overall average salary in the dataset is:

**63,375**

Department-level maximum salaries include:

| Department | Maximum Salary |
| ---------- | -------------: |
| Finance    |         72,000 |
| HR         |         80,000 |
| IT         |         65,000 |
| Marketing  |         55,000 |

### 4. City Analysis

Employee distribution across cities is analysed using `value_counts()`.

The dataset contains employees from:

* New York
* San Diego
* Chicago
* Boston

Each city has two employees in the dataset.

### 5. Gender and Age Analysis

The average age of female employees is calculated using filtering and aggregation.

**Average age of female employees: 29.5 years**

### 6. Sorting

Employee records are sorted based on:

* Salary
* Department
* Age

Salary sorting is used to identify employees with higher and lower salaries.

### 7. Group-Based Analysis

The project identifies the youngest employee within each department using:

```python
df.loc[df.groupby('Department')['Age'].idxmin()]
```

This combines grouping, aggregation, and row selection to retrieve the corresponding employee records.

### 8. Date Analysis

The `JoinDate` column is converted into Pandas datetime format.

The project uses date properties to identify employees who joined after 2020 and finds the most recently joined employee.

The most recent joining record in the dataset belongs to:

**Diana — IT — 17 May 2022**

### 9. Experience Feature Engineering

A new `Year_Experience` column is created from the employee's joining date:

```python
df['Year_Experience'] = (
    pd.Timestamp.now() - df['JoinDate']
).dt.days // 365
```

This provides an approximate number of years since each employee joined.

### 10. Salary Transformation

A new salary representation is created in lakhs:

```python
df['Salary_in_Lakhs'] = df['Salary'] / 100000
```

This converts salary values from their original units into lakhs.

### 11. Employee Seniority Classification

Employees are classified based on age using a custom function:

```python
def seniority(age):
    if age < 30:
        return 'Junior'
    elif 30 <= age <= 40:
        return 'Mid'
    else:
        return 'Senior'
```

The resulting categories are:

* Junior
* Mid
* Senior

## Key Results

The analysis produced several employee-level and department-level observations:

* Average employee salary: **63,375**
* Average employee age: **32.75**
* Average female employee age: **29.5**
* HR has the highest maximum salary in the dataset at **80,000**
* The dataset contains four cities with two employees each
* Diana has the most recent joining date
* The youngest employee in each department was identified using group-based analysis
* Additional analytical features were created for experience, salary in lakhs, and seniority

## Technologies Used

* Python
* Pandas
* Microsoft Excel dataset
* Google Colab / Jupyter Notebook

## Pandas Concepts Practiced

This project demonstrates practical usage of:

* `read_excel()`
* `head()`
* `columns`
* `dtypes`
* `shape`
* `isnull()`
* Boolean filtering
* `isin()`
* `pd.to_datetime()`
* Datetime properties
* `mean()`
* `groupby()`
* `max()`
* `value_counts()`
* `sort_values()`
* `idxmin()`
* `idxmax()`
* `loc[]`
* Custom functions with `apply()`
* Feature engineering
* Arithmetic transformations

## Project Structure

```text
Employee-Data-Analysis-Pandas/
│
├── pandas_employee_analysis.ipynb
├── pandas_new.xlsx
└── README.md
```

## Limitations

This project uses a small employee dataset, so the results are intended for Pandas practice and demonstration rather than statistical conclusions about a larger workforce.

The `Year_Experience` calculation is based on the execution date of the notebook and therefore changes as time passes.

## Skills Demonstrated

* Data loading
* Data inspection
* Data quality checking
* Data filtering
* Aggregation
* GroupBy analysis
* Sorting
* Date and time manipulation
* Feature engineering
* Custom functions
* Basic employee segmentation
* Pandas-based exploratory analysis

## Author

**Nayanendhu CU**

GitHub: https://github.com/nayanendhucu

LinkedIn: https://www.linkedin.com/in/nayanendhu-unnikrishnan/
