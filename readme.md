# Personal Finance Intelligence

An exploratory data analysis project that analyzes personal income, expenses, savings, spending patterns, and payment methods using Python and popular data science libraries.

## Project Overview

The goal of this project is to understand personal financial behavior through data analysis and visualization.

The project uses a small expense dataset containing income and expense transactions. It calculates important financial statistics and creates visualizations to identify spending patterns and savings.

## Features

* Calculate total income
* Calculate total expenses
* Calculate savings
* Calculate savings percentage
* Identify the highest spending category
* Identify the largest and smallest transactions
* Calculate average and median expenses
* Analyze expenses by category
* Analyze expenses by payment method
* Calculate monthly income and expenses
* Compare monthly income and expenses
* Calculate expense percentages
* Calculate savings percentage
* Analyze correlation between monthly income and expenses
* Create charts using Matplotlib and Seaborn

## Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Jupyter Notebook

## Project Structure

```text
Personal-Finance-Intelligence/
│
├── data/
│   └── expenses.csv
│
├── notebooks/
│   └── personal_finance.ipynb
│
├── README.md
```

## Dataset Description

The dataset contains the following columns:

| Column           | Description                |
| ---------------- | -------------------------- |
| `date`           | Date of the transaction    |
| `category`       | Expense or income category |
| `amount`         | Transaction amount         |
| `type`           | Income or Expense          |
| `payment_method` | Bank, UPI, Card, or Cash   |

Example categories include:

* Salary
* Food
* Transport
* Shopping
* Entertainment
* Rent

## Analysis Workflow

### 1. Data Loading

The dataset is loaded using Pandas.

```python
import pandas as pd
import numpy as np

df = pd.read_csv("../data/expenses.csv")
```

### 2. Data Inspection

The dataset is inspected using:

```python
df.shape
df.columns
df.info()
df.isnull().sum()
df.describe()
```

### 3. Income and Expense Analysis

Total income and expenses are calculated using filtering and aggregation.

```python
total_income = df.loc[df["type"] == "Income", "amount"].sum()

total_expenses = df.loc[
    df["type"] == "Expense",
    "amount"
].sum()

savings = total_income - total_expenses
```

### 4. Category Analysis

Expenses are grouped by category to identify spending patterns.

```python
expenses = df.loc[df["type"] == "Expense"]

expense_by_category = (
    expenses.groupby("category")["amount"]
    .sum()
)
```

### 5. Statistical Analysis

The project calculates:

* Mean
* Median
* Minimum
* Maximum
* Range
* Percentage distribution
* Average expense by category

```python
average_expense = np.mean(expenses["amount"])

median_expense = np.median(expenses["amount"])

expense_range = (
    expenses["amount"].max()
    - expenses["amount"].min()
)
```

### 6. Monthly Analysis

The transaction date is converted into a datetime format.

```python
df["date"] = pd.to_datetime(df["date"])

df["month"] = df["date"].dt.month_name()
```

Monthly income and expenses are then calculated using `groupby()`.

### 7. Visualization

The project creates different charts, including:

* Expenses by category
* Expense distribution
* Expenses by payment method
* Monthly income versus expenses
* Category-wise average expenses

Example:

```python
import matplotlib.pyplot as plt

plt.bar(
    expense_by_category.index,
    expense_by_category.values
)

plt.title("Expenses by Category")
plt.xlabel("Category")
plt.ylabel("Amount Spent")
plt.xticks(rotation=45)
plt.show()
```

## Key Insights

The analysis helps answer questions such as:

* How much money was earned?
* How much money was spent?
* How much money was saved?
* Which category consumed the most money?
* Which payment method was used most frequently?
* What was the average expense?
* What was the largest transaction?
* How did expenses change from month to month?
* What percentage of income was spent?
* What percentage of income was saved?

## Important Statistical Note

Correlation between monthly income and expenses may return `NaN` when income remains constant across all months.

This happens because correlation requires variation in both variables. If income is the same every month, its standard deviation is zero, so the correlation cannot be calculated meaningfully.

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/personal-finance-intelligence.git
```

### 2. Move into the project folder

```bash
cd personal-finance-intelligence
```

### 3. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

Open:

```text
notebooks/personal_finance.ipynb
```

Run the cells in order.

## Learning Outcomes

Through this project, I practiced:

* Loading and inspecting datasets
* Filtering DataFrames
* Selecting rows and columns
* Grouping data using `groupby()`
* Using aggregation functions
* Calculating statistics with NumPy
* Working with dates
* Performing basic financial analysis
* Creating data visualizations
* Understanding correlation
* Writing a complete exploratory data analysis project

## Future Improvements

Possible future improvements include:

* Adding more months of transaction data
* Adding a budget limit for each category
* Detecting overspending
* Creating a monthly savings prediction
* Adding interactive dashboards
* Using real-world anonymized financial data
* Adding automatic expense categorization
* Building a simple Streamlit dashboard

## Limitations

* The dataset is small and manually created.
* The analysis is descriptive and does not use machine learning.
* The results depend on the quality of the dataset.
* Correlation does not prove causation.

## Conclusion

Personal Finance Intelligence demonstrates how Python, NumPy, Pandas, Matplotlib, and Seaborn can be used to analyze financial data and convert raw transactions into meaningful insights.

This project helped strengthen the foundations of data analysis, statistics, mathematical implementation, and data visualization before starting core machine learning algorithms.

## Author

**Niharika**

B.Tech CSE — Artificial Intelligence and Machine Learning
