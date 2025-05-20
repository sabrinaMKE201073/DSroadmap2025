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

---

## 🔗 Correlation

• Describes direction and strength of relationship between two variables
• Can help us use variables to predict future outcomes

1) Pandas `.corr()` method
> calculates Pearson correlation coefficient, measuring linear relationship.

```python
divorce.corr()
```

<left>
  <img src="correlation.JPG" width="500">
</left>

📌 *A value closer to zero is indicative of a weak relationship, while values closer to one or negative one indicate stronger relationships.*

2) Correlation heatmap (`.heatmap`)
> A correlation heatmap is a visual way to show how strongly different variables in your dataset are related to each other. The values range from:
- +1: Strong positive correlation (as one increases, the other increases)
- 0: No correlation
- -1: Strong negative correlation (as one increases, the other decreases)

The color helps you spot these relationships easily:

👍🏼 Light colors (like beige) = strong positive correlation

🍇 Dark colors (like deep purple/black) = strong negative correlation

```python
sns.heatmap(divorce.corr(), annot=True)
plt.show()
```

<left>
  <img src="heatmap.JPG" width="500">
</left>

📌 *Here, we can see that marriage year and marriage duration are strongly negatively correlated whith value of -0.81; 

### Correlation in context
```python
divorce["divorce_date"].min() #Output: Timestamp ('2000-01-08 00:00:00')
divorce["divorce_date"].max() #Output: Timestamp ('2015-11-03 00:00:00')
```

📌 Keypoint: Since our dataset is about marriages that ended between 2000 to 2015, marriages that started in earlier years will by definition have a longer duration compared to those that started in later ones.

---

### Visualizing realtionship

- Pearson coefficient we've been looking at only describes the linear correlation between variables.
- Variables can have a strong non-linear relationship and a Pearson correlation coefficient of close to zero. 
- This is why it's important to complement our correlation calculations with other plots (such as scatter plot

<left>
  <img src="v_r.JPG" width="500">
</left>

---

### Pairplots
> - Next level of scatterplots
> - useful for quick overview of relationships within dataset
> - dificult to interpret especially with big datasets
> - pairplot plots all pairwise relationships between numerical variables in one visualization. 

```python
sns.pairplot(data=divorce)
plt.show()
```

<left>
  <img src="overview_plots.JPG" width="500">
</left>

---

### Limiting Pairplots
> We can limit the number of plotted relationships by setting the vars argument equal to the variables of interest.

```python
sns.pairplot(data=divorce, vars=["income_man", "income_woman", "marriage_duration"])
```
<left>
  <img src="negativecorrelation.JPG" width="500">
</left>

📌 Keypoint: When we compare how income of husband, income of wife, and marriage duration relate to one another, there is no strong visible trend. In the scatterplots (from the pairplot), the points are likely scattered randomly, not forming a clear line or curve. hence,  income doesn’t seem to strongly influence marriage length.

---

## 🎯 Factor relationships & distributions

> In this chapter, let's see how categorical variable related to education of man affect the marriage duration.
> Next, we will see the relationship between marriage age and education

## PART 1
### 1) Level of education: male partner using '.value_counts()`

```python
divorce["education_man"].value_counts()
```
<left>
  <img src="count_education.JPG" width="300">
</left>

📌 Keypoint: most men have an education level between primary and professional, with a few men in the "None" or "Other" categories.

### 2) Exploring categorical relationships using `.histplot`

```python
sns.histplot(data=divorce,
            x="marriage_duration",
            hue="education_man",
            binwidth=1) 
plt.show() 
```
<left>
  <img src="hist_hue_edu.JPG" width="500">
</left>

📌 Since education levels are stacked on top of each other, the relationship between marriage duration and male education level isn't super clear.

### 3) Kernel Density Estimate (KDE) plots
> Similiar to histogram, KDE allow us to visualize distributions.
> KDE are more interpretable, though, especially when multiple distributions are shown.

```python
sns.kdeplot(data=divorce,
            x="marriage_duration",
            hue="education_man") 
plt.show() 
```
<left>
  <img src="kde.JPG" width="500">
</left>

📌 Notice that the location of the peak marriage duration for each level of the male partner's education is more identifiable in this KDE plot than it was in the histogram. However, due to the smoothing algorithm used in KDE plots, the curve can include values that don't make sense, so it's important to set good smoothing parameters.
📌 zooming in on the KDE plot showing the distribution of male education levels, we can see that the distribution seems to suggest that some couples had marriage durations of less than zero which is impossible.

---

### 4) Fix KDE plots using `cut` keyword argument

```python
sns.kdeplot(data=divorce,
            x="marriage_duration",
            hue="education_man"
            cut=0) 
plt.show() 
```
<left>
  <img src="cut0.JPG" width="500">
</left>

📌 When we set cut equal to zero, the curve will be limited to values between the minimum and maximum x values, Hence, The plot now shows only marriage durations greater than or equal to one year, the shortest marriage duration in the dataset.

### 5) Cumulative KDE plots 
> This will give cumulative distribution function, we can set the cumulative keyword argument to True. 

```python
sns.kdeplot(data=divorce,
            x="marriage_duration",
            hue="education_man"
            cut=0,
            cumulative=True) 
plt.show() 
```
<left>
  <img src="cum1.JPG" width="500">
</left>

---

## PART 2
###  Is there a relationship between age at marriage and education level?
> We can create columns representing the approximate age at marriage for men and women by subtracting each partner's birth year from the marriage year.

```python
divorce["man_age_marriage"] = divorce["marriage_year"] - divorce["dob_man"].dt.year 
divorce["woman_age_marriage"] = divorce["marriage_year"] - divorce["dob_woman"].dt.year
```

### 1) Scatter plot with categorical variables

```python
sns.scatterplot(data=divorce,  
                x="woman_age_marriage", 
                y="man_age_marriage",  
                hue="education_man") 
plt.show() 
```
<left>
  <img src="scatter_age.JPG" width="500">
</left>

📌 The results suggest that men with a professional education level, represented with orange dots, may tend to get married later


