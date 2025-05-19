# 📊 **Relationships in Data using Pandas & Seaborn**

---

## 🕰️ **Patterns Over Time**

Understanding how data changes over time is crucial for spotting trends and seasonal patterns. First, we must ensure that any time-based column is in the correct datetime format.

---

### 🧹 **Step 1: Fix Date & Time Data Types**

> 📝 *Pandas often misinterprets date/time columns as string (`object`) types. Converting them to `datetime` is essential for time-based analysis.*

---

#### ✅ Option 1: Use `parse_dates` in `pd.read_csv()`

Converts a column into `datetime` **while importing** the CSV.

```python
divorce = pd.read_csv("divorce.csv", parse_dates=["marriage_date"])
divorce.dtypes  # marriage_date should now be datetime64
```

---

#### ✅ Option 2: Use `pd.to_datetime()` after import

Convert the column to datetime **after loading** the dataset.

```python
divorce["marriage_date"] = pd.to_datetime(divorce["marriage_date"])
```

---

### 🛠️ **Step 2: Creating a DateTime Column from Multiple Columns**

Sometimes, you have separate columns for month, day, and year. Combine them like this:

```python
divorce["marriage_date"] = pd.to_datetime(divorce[["month", "day", "year"]])
```

<left>
  <img src="datetime.JPG" width="350">
</left>

---

### 🔍 **Step 3: Extract Specific Date Parts**

Use `.dt` accessor to extract components like month, year, or day.

```python
divorce["marriage_month"] = divorce["marriage_date"].dt.month
divorce.head()
```

<left>
  <img src="dt.month.JPG" width="350">
</left>

---

## 📈 **Visualizing Patterns Over Time: Line Plot**

> A line plot is useful to show how a numeric variable changes over time. It aggregates y-values and shows a confidence interval by default.

```python
sns.lineplot(data=divorce, x="marriage_month", y="marriage_duration")
plt.show()
```

<left>
  <img src="result_lineplot.JPG" width="500">
</left>

---

### 📌 **Interpretation:**

- The blue **line** shows the mean `marriage_duration` for each `marriage_month`.
- The shaded **confidence interval (CI)** area reflects a 95% probability that the true mean falls within that range.
- A **wide CI** implies high variability—consider exploring deeper (e.g., check for outliers or additional grouping).


## 🔗 Correlation

## 🎯 Factor relationships & distributions
