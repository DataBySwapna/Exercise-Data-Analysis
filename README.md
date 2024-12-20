# 🏋️ Exercise Data Analysis
![image](https://github.com/user-attachments/assets/2e2aa2ee-5bd4-42a5-b1f3-e0c726fa0a5e)
This project demonstrates data analysis on an **exercise dataset** using Python. The goal is to clean the data, perform descriptive analysis, and visualize insights to better understand the relationship between variables like pulse, calories burned, and session durations.
---
## 🛠️ Tools Used
- **Python**: Programming language for data analysis.
- **Pandas**: For data manipulation and cleaning.
- **Matplotlib**: For data visualization.
---
🎯 Key Insights
1.	The average calories burned per session were calculated.
2.	Pulse data was cleaned to remove missing values.
3.	Relationships between Pulse and Calories were visualized, showing a positive correlation.
4.	The dataset was successfully cleaned and saved for future use
________________________________________
## 📋 Steps in the Analysis
### Load the Dataset
```python
import pandas as pd
import matplotlib.pyplot as plt
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
## Line Plot: Calories Burned Over SessionsTrends in calories burned across sessions.
```python
plt.figure(figsize=(10, 5))
plt.plot(df["ID"], df["Calories"], label="Calories Burned")
plt.title("Calories Burned Over Sessions")
plt.xlabel("Session ID")
plt.ylabel("Calories")
plt.legend()
plt.show()
```
   ![image](https://github.com/user-attachments/assets/169dbce9-4f3b-41e9-888a-1d40ecefc846)
## Histogram: Pulse Distribution
Distribution of pulse rates.
```python
plt.figure(figsize=(8, 5))
plt.hist(df["Pulse"], bins=20, color="skyblue", edgecolor="black")
plt.title("Pulse Distribution")
plt.xlabel("Pulse")
plt.ylabel("Frequency")
plt.show()
```
   ![image](https://github.com/user-attachments/assets/2884db7b-8a78-4aca-a093-54cf067eb636)
## Scatter Plot: Pulse vs Calories
Relationship between pulse and calories burned.
```python
plt.figure(figsize=(8, 5))
plt.scatter(df["Pulse"], df["Calories"], color="green", alpha=0.5)
plt.title("Pulse vs Calories")
plt.xlabel("Pulse")
plt.ylabel("Calories")
plt.show()
```
   ![image](https://github.com/user-attachments/assets/a8b0ea78-e071-455b-9c26-da184bda1a32)
## Bar Plot: Average Calories by Duration
Average calories burned based on session duration.
```python
df.groupby("Duration")["Calories"].mean().plot(kind="bar", color="orange")
plt.title("Average Calories by Duration")
plt.xlabel("Duration (minutes)")
plt.ylabel("Average Calories")
plt.show()
```
   ![image](https://github.com/user-attachments/assets/c13612c5-ab2d-4217-93f6-05bc2668c6ec)
### Save the Cleaned Dataset
```python
# Save the cleaned dataset to a new Excel file
df.to_excel("Cleaned_Exercise_Data.xlsx", index=False)
print("Cleaned dataset saved to 'Cleaned_Exercise_Data.xlsx'")
```
📂 Project Files
1.	Exercise_Data_With_ID.xlsx: Original dataset.
2.	Cleaned_Exercise_Data.xlsx: Cleaned dataset saved after processing.
