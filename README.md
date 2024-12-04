# 🏋️ Exercise Data Analysis

This project demonstrates data analysis on an **exercise dataset** using Python. The goal is to clean the data, perform descriptive analysis, and visualize insights to better understand the relationship between variables like pulse, calories burned, and session durations.

---

## 🛠️ Tools Used
- **Python**: Programming language for data analysis.
- **Pandas**: For data manipulation and cleaning.
- **Matplotlib**: For data visualization.

🎯 Key Insights
1.	The average calories burned per session were calculated.
2.	Pulse data was cleaned to remove missing values.
3.	Relationships between Pulse and Calories were visualized, showing a positive correlation.
4.	The dataset was successfully cleaned and saved for future use.
________________________________________
📊 Visualizations
1.	Line Plot: Trends in calories burned across sessions.
2.	Histogram: Distribution of pulse rates.
3.	Scatter Plot: Relationship between pulse and calories burned.
4.	Bar Plot: Average calories burned based on session duration.
________________________________________
📂 Project Files
1.	Exercise_Data_With_ID.xlsx: Original dataset.
2.	Cleaned_Exercise_Data.xlsx: Cleaned dataset saved after processing.

## 📋 Steps in the Analysis

### Step 1: Load the Dataset
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = "Exercise_Data_With_ID.xlsx"
df = pd.read_excel(file_path)

# Display the first few rows
print(df.head())






### Load the Dataset
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = "Exercise_Data_With_ID.xlsx"
df = pd.read_excel(file_path)

# Display the first few rows
print(df.head())
```
### Explore the Dataset
# Get dataset info and summary statistics
```python
print(df.info())
print(df.describe())
```
### Data Cleaning
``` python
# Fill missing values in numeric columns with the mean
df["Pulse"].fillna(df["Pulse"].mean(), inplace=True)
df["Maxpulse"].fillna(df["Maxpulse"].mean(), inplace=True)
df["Calories"].fillna(df["Calories"].mean(), inplace=True)

# Fill missing values in date column with a placeholder
df["Date"].fillna("Unknown", inplace=True)
```
### Descriptive Analysis
``` python
# Calculate basic statistics
print("Mean Calories Burned:", df["Calories"].mean())

# Group by Duration and calculate mean Calories
print(df.groupby("Duration")["Calories"].mean())
```
### Data Visualization
Line Plot: Calories Burned Over Sessions
```python

plt.figure(figsize=(10, 5))
plt.plot(df["ID"], df["Calories"], label="Calories Burned")
plt.title("Calories Burned Over Sessions")
plt.xlabel("Session ID")
plt.ylabel("Calories")
plt.legend()
plt.show()
```
Histogram: Pulse Distribution
```python
`
plt.figure(figsize=(8, 5))
plt.hist(df["Pulse"], bins=20, color="skyblue", edgecolor="black")
plt.title("Pulse Distribution")
plt.xlabel("Pulse")
plt.ylabel("Frequency")
plt.show()
```
Scatter Plot: Pulse vs Calories
```python

plt.figure(figsize=(8, 5))
plt.scatter(df["Pulse"], df["Calories"], color="green", alpha=0.5)
plt.title("Pulse vs Calories")
plt.xlabel("Pulse")
plt.ylabel("Calories")
plt.show()
```
Bar Plot: Average Calories by Duration
```python

df.groupby("Duration")["Calories"].mean().plot(kind="bar", color="orange")
plt.title("Average Calories by Duration")
plt.xlabel("Duration (minutes)")
plt.ylabel("Average Calories")
plt.show()
```
Step 6: Save the Cleaned Dataset
```python
# Save the cleaned dataset to a new Excel file
df.to_excel("Cleaned_Exercise_Data.xlsx", index=False)
print("Cleaned dataset saved to 'Cleaned_Exercise_Data.xlsx'")
```
