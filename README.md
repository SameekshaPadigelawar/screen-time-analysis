# DAV-ASSIGNMENT-1(162)
 

 📊 Screen Time Analysis – Data Analysis Project

This project performs an in-depth analysis of the **Screen Time Dataset** using Python. The goal is to explore screen time behavior, uncover insights, and demonstrate key data analysis techniques using **NumPy**, **Pandas**, **Matplotlib**, and **Seaborn**.


🧾 Dataset Overview

The dataset captures screen time habits of individuals, with key attributes such as:

- **ID**: Unique identifier for each participant  
- **Gender**: 0 = Male, 1 = Female  
- **Age**: Age of the individual  
- **Daily Screen Time**: Number of hours spent on screen daily  
- **Social Media Usage**: Average daily time on social media  
- **Productivity Score**: Self-reported productivity level  
- **Sleep Hours**: Average sleep duration in hours  
- **Stress Level**: Reported stress level (1 to 10 scale)

 🔧 Operations Performed

#### 📥 Data Loading and Inspection
- Loaded data using `pandas.read_csv()`
- Inspected with `.head()`, `.info()`, `.describe()`
- Checked for null or missing values
- Verified column data types

#### 🧮 NumPy & Pandas Operations
- **Array slicing** from DataFrame values
- **Universal functions** like `np.square`, `np.exp`, `np.log`
- **Aggregation functions**: `mean()`, `sum()`, `std()`, etc.
- **Broadcasting**: Performed arithmetic operations across rows/columns
- **Boolean masking**: Filtered data (e.g., age > 25, high screen time)
- **Sorting and argsort**: Sorted users by screen time and productivity
- **Partial sorting**: Retrieved top N social media users
- **Structured arrays**: Created structured NumPy arrays from select columns
- **Multi-indexing**: Applied hierarchical indexing with Pandas

---

### 🔍 Feature Engineering

- Added new feature:  
  `Screen_Time_Efficiency = Productivity Score / Daily Screen Time`
- Normalized Age using Z-score:
  ```python
  df['Age_z'] = (df['Age'] - df['Age'].mean()) / df['Age'].std()
  ```
- Created custom subsets:
  - High social media users
  - Productive individuals (score > 7)
  - Sleep-deprived users (sleep < 6 hrs)


### 📊 GroupBy Aggregation

- **By Gender**: Avg. screen time, sleep hours, stress
- **By Age Group**: Grouped into ranges (e.g., 18–25, 26–35)
- **By Productivity**: Avg. screen time, stress level
- Used `groupby().agg()` for multiple aggregations

---

### 📈 Pivot Tables

Generated pivot tables for summary views:

- **Screen Time by Gender**:
  ```python
  pd.pivot_table(df, index='Gender', values='Daily Screen Time', aggfunc='mean')
  ```

- **Sleep Hours by Age Group**:
  ```python
  pd.pivot_table(df, index='Age Group', values='Sleep Hours', aggfunc='mean')
  ```

- **Stress Level by Productivity Score and Gender**:
  ```python
  pd.pivot_table(df, index='Productivity Score', columns='Gender', values='Stress Level', aggfunc='mean')
  ```



 🔄 Dataset Merging

- Simulated split of lifestyle and performance data
- Merged datasets using `pd.merge()` on `ID`

---

📊 Data Visualization

Used Seaborn and Matplotlib to visualize insights:

- **Histogram of Age**:
  ```python
  sns.histplot(df['Age'], kde=True)
  ```

- **Box Plot of Screen Time by Gender**:
  ```python
  sns.boxplot(x='Gender', y='Daily Screen Time', data=df)
  ```

- **Bar Plot of Avg. Productivity per Age Group**:
  ```python
  sns.barplot(x='Age Group', y='Productivity Score', data=grouped_df)
  ```

- **Line Plot of Sleep vs. Screen Time**:
  ```python
  sns.lineplot(x='Sleep Hours', y='Daily Screen Time', data=df)
  ```


 ▶️ How to Run

1. Place the CSV file `screen_time_dataset.csv` in your working directory.
2. Open and run the Jupyter notebook (`screen_time_analysis.ipynb`).
3. Install required libraries:
   ```
   pip install pandas numpy matplotlib seaborn
   ```

 🎓 Summary

This project demonstrates skills in:

- Core data analysis using Pandas and NumPy
- Feature engineering and normalization
- Group-based and pivot table analytics
- Dataset merging and multi-indexing
- Data visualization for pattern recognition

 
