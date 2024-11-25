# Basic Data Analysis and Visualization
# Description
This script demonstrates how to:

Load a CSV file into a pandas DataFrame.
Perform basic data analysis (mean, median, and mode).
Visualize results using matplotlib (histogram and scatter plot).
Code
python
Copy code
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from collections import Counter

# Load CSV file
try:
    data = pd.read_csv("data.csv")
    print("Data loaded successfully!")
except FileNotFoundError:
    print("The file 'data.csv' was not found.")
    exit()

# Display the first few rows
print("First 5 rows of the data:")
print(data.head())

# Basic Data Analysis
# Calculate Mean
ages = data["Age"]
salaries = data["Salary"]

mean_age = np.mean(ages)
mean_salary = np.mean(salaries)
print("\n--- Mean Values ---")
print(f"Mean Age: {mean_age}")
print(f"Mean Salary: {mean_salary}")

# Calculate Median
median_age = np.median(ages)
median_salary = np.median(salaries)
print("\n--- Median Values ---")
print(f"Median Age: {median_age}")
print(f"Median Salary: {median_salary}")

# Calculate Mode
def calculate_mode(column):
    counter = Counter(column)
    mode_value, count = counter.most_common(1)[0]
    return mode_value

mode_age = calculate_mode(ages)
mode_salary = calculate_mode(salaries)
print("\n--- Mode Values ---")
print(f"Mode Age: {mode_age}")
print(f"Mode Salary: {mode_salary}")

# Visualization
# Plot Age Distribution
plt.figure(figsize=(10, 5))
plt.hist(ages, bins=5, color='skyblue', alpha=0.7, rwidth=0.85)
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.grid(axis='y', alpha=0.75)
plt.show()

# Scatter Plot for Salary
plt.figure(figsize=(10, 5))
plt.scatter(data["Age"], data["Salary"], color='green', alpha=0.6)
plt.title("Salary vs Age")
plt.xlabel("Age")
plt.ylabel("Salary")
plt.grid(True)
plt.show()
Prerequisites
Python 3.x installed on your system.
Install required libraries using:
bash
Copy code
pip install pandas numpy matplotlib
Ensure the file data.csv is present in the same directory as the script.
How to Run
Save the script as analysis.py.
Place your data.csv file in the same directory.
Execute the script:
bash
Copy code
python analysis.py
Output
Mean, Median, Mode:
The script calculates and prints the mean, median, and mode of the Age and Salary columns.
Visualizations:
Age Distribution: A histogram showing the frequency of ages.
Salary vs Age: A scatter plot visualizing the relationship between age and salary.
Example CSV File
Below is an example of what data.csv should look like:

csv
Copy code
Name,Age,Salary
Alice,25,50000
Bob,30,60000
Charlie,35,70000
Diana,28,65000
Evan,40,80000
