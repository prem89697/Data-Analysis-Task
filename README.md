# Data-Analysis-Task
# Using the Pandas library, load a CSV file and perform basic data analysis tasks, such as   calculating the average of a selected column. Additionally, use Matplotlib to create   visualizations, including bar charts, scatter plots, and heatmaps, to analyze the data. Provide   insights and observations based on the analysis and visualizations.
# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load CSV
# df = pd.read_csv("data.csv")
df = pd.read_csv("C:\\Users\\premp\\OneDrive\\Coding\\internship\\data.csv")

# First 5 rows
print("First 5 rows of dataset:")
print(df.head())

# Dataset info
print("\nDataset Info:")
print(df.info())

# Descriptive statistics
print("\nDescriptive Statistics:")
print(df.describe())

# -------------------------------
# 1. Average Age and Salary
avg_age = df["Age"].mean()
avg_salary = df["Salary"].mean()
print(f"\nAverage Age: {avg_age:.2f}")
print(f"Average Salary: {avg_salary:.2f}")

# -------------------------------
# 2. Bar Chart - Average Salary by Department
plt.figure(figsize=(6,4))
df.groupby("Department")["Salary"].mean().plot(kind="bar", color="skyblue")
plt.title("Average Salary by Department")
plt.ylabel("Average Salary")
plt.show()

# -------------------------------
# 3. Scatter Plot - Age vs Salary
plt.figure(figsize=(6,4))
plt.scatter(df["Age"], df["Salary"], alpha=0.7, color='green')
plt.title("Scatter Plot: Age vs Salary")
plt.xlabel("Age")
plt.ylabel("Salary")
plt.show()

# -------------------------------
# 4. Heatmap - Correlation
plt.figure(figsize=(6,4))
sns.heatmap(df[["Age","Salary"]].corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Correlation Heatmap (Age vs Salary)")
plt.show()

# -------------------------------
# Insights (to include in report)
"""
1. Average Age of employees is around 31 years, and Average Salary is ~52,000.
2. IT department salaries are slightly lower compared to Finance.
3. Scatter plot shows that as Age increases, Salary also tends to increase (positive correlation).
4. Heatmap confirms a positive correlation between Age and Salary.
"""

