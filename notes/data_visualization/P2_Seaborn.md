
# 📊 Relation Plot & Subplots with Seaborn

## 1. `relplot()` Overview
- A relational plot function that creates either scatter or line plots.
- Supports creation of subplots in a single figure.

---

## 📍 Subplots 1: Column Example

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.relplot(x="total_bill",
              y="tip",
              data=tips,
              kind="scatter",
              col="smoker")
plt.show()
```
<left>
  <img src="smoker_nonsmoker.JPG" alt="subplot for smoker vs non smoker" width="300">
</left>

---

## 📍 Subplots 2: Row Example

```python
sns.relplot(x="total_bill",
              y="tip",
              data=tips,
              kind="scatter",
              row="smoker")
```
<left>
  <img src="subplots2.JPG" alt="subplot for smoker vs non smoker in row" width="200">
</left>

---

## 📍 Subplots 3: Combination of Column and Row

```python
sns.relplot(x = "total_bill",
               y= "tip",
               data = tips,
               kind = "scatter",
               col = "smoker",
               row = "time")
```
<left>
  <img src="combine_subplots.JPG" alt="subplot for smoker and time during lunch or dinner" width="300">
</left>

---

## 📍 Subplots 4: Customizing Subplots Layout

```python
sns.relplot(x = "total_bill",
               y= "tip",
               data = tips,
               kind = "scatter",
               col="day",
               col_wrap=2,
               col_order=["Thur", "Fri", "Sat", "Sun"])
```
<left>
  <img src="subplots_days.JPG" alt="subplot daily in specific order" width="300">
</left>

---

## 📍 Exercise: Creating Two-Factor Subplots

```python
sns.relplot(x="G1", y="G3", 
            data=student_data,
            kind="scatter", 
            col="schoolsup",
            col_order=["yes", "no"],
            row = "famsup",
            row_order=["yes", "no"])
```
<left>
  <img src="two_factors.JPG" alt="creating two factor subplots" width="300">
</left>

📌 *The first semester grade does correlate with the final grade, regardless of the support received.*

---

## 2. 🎨 Customizing Scatter Plots (size, hue, style, alpha)
- Enhances visual contrast and analysis

### 📍 Exercise 1: Horsepower vs Fuel Efficiency

```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.relplot(x="horsepower", y="mpg", 
            data=mpg, kind="scatter", 
            size="cylinders",
            hue="cylinders")
plt.show()
```
<left>
  <img src="horsepower_plot.JPG" alt="vary the color of points by no. of cylinder" width="400">
</left>

📌 *Cars with higher horsepower tend to get lower MPG and often have more cylinders.*

---

### 📍 Exercise 2: Acceleration vs MPG by Country

```python
sns.relplot(x="acceleration", y="mpg", 
            data=mpg, kind="scatter",
            hue="origin",
            style="origin")
```
<left>
  <img src="acceleration_country.JPG" alt="how fast a car can accelerate at different country" width="400">
</left>

📌 *USA cars tend to accelerate faster but get lower MPG compared to Europe and Japan.*

---

## 🔄 Two Types of Relational Plots

### Scatter plots
- Each point is an independent observation

### Line plots
- Each point represents the same object tracked over time

---

### 📍 Example for Line plot

```python
sns.relplot(x="hour",
            y="NO_2_mean",
            data=air_df_loc_mean,
            kind="line",
            style="location",
            hue="location")
```
![air pollution by location](airpollution.JPG)

📌 *South region tends to have slightly higher average Nitrogen Dioxide levels compared to other regions*

---

### 📍 Adjusting line style

```python
markers=True #to display marker for each data point
dashes=False #change line style to exact line
```

<left>
  <img src="line.JPG" alt="line style" width="300">
</left>

---

### 📍 Multiple observation per x-value (Visualize a confidence interval)

```python
sns.relplot(x="hour", y="NO_2",
            data=air_df,
            kind="line")
```
<left>
  <img src="shaded_1.JPG" alt="line style" width="250">
</left>

📌 Key Points:
- When x-values repeat, Seaborn calculates the mean automatically.
- The shaded area shows the 95% confidence interval (CI).
- CI tells us the range where the true average likely falls.
- Wider shaded areas = more uncertainty in the average.

---

### 📍 How measurement of NO2 varied across different collection station at a given time

```python
ci = "sd"
#to turn off the ci, can set it to "None"
```
<left>
  <img src="sd_ci.JPG" width="250">
</left>

📌 *shaded area this time will represents the standard deviation, which shows the spread of the distribution of observations at each x value.*

---

### 📍 Plotting subgroups in line plots

```python
sns.relplot(x="model_year", 
            y="horsepower", 
            data=mpg, 
            kind="line", 
            ci=None, #turn off the ci
            style = "origin", #various of style
            hue = "origin", #various of color
            markers=True, #marker style for each line
            dashes=False) #solid lines
```
<left>
  <img src="off_ci_diffcountry.JPG" width="350">
</left>

📌 *We can see that this downward trend in horsepower was more pronounced among cars from the USA*

---




