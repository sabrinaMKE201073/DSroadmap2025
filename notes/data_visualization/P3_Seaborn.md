# 🧮 Visualizing Categorical and Quantitative Variable 📊
---

## 🔢 1) Count plots and bar plots
- categorical variable
- eg: count plots, bar plots
- comparisons between groups

### 📍 Count plot using catplot() function

  ```python
  category_order = ["No answer","Not at all","Not very","Somewhat","Very"]

  sns.catplot(x="how_masculine",
              data=masculinity_data,
              kind="count",
              order=category_order)

  plt.show()
  ```
  <left>
    <img src="change_order.JPG" alt="order of masculinity example" width="350">
  </left>

💡 *Based on the order of the masculinity from not masculine to very masculine, we can see that the bar plot shown the majority of the dog masculinity is under category of somewhat masculine type*

---

### 📍 Bar plots using catplot() function
- display the mean of quantitative variable per category

  ```python
  sns.catplot(x="day",
              y="total_bills",
              data = tips,
              kind="bar")
  ```
  <left>
    <img src="bar_plot1.JPG" alt="bar plot example" width="300">
  </left>
  
  ### 💡 Key points:
  - *The highest total bill obtained on Sunday whereas the lowest bill is on Friday*
  - *Lines at the centre of each bar showed the confidence intervals for these mean*

  ```python
  #to turn off the auto confidence interval lines,
  #set ci to None
  ci = None
  ```

---

  ### 📍 Exercise: Count plots
  
  ```python
  sns.catplot(y="Internet usage", 
              data=survey_data,
              kind="count",
              col="Age Category")
  ```
  <left>
    <img src="phoneusage.JPG" alt="survey on internet usage" width="500">
  </left>

  💡 Based on the plots, we can observe that:
  
  - *Most individuals use the internet for a few hours each day, and this trend is consistent across all   age groups.*
  - *However, younger individuals (under 21 years old) tend to spend more time online compared to those aged 21 and above.*

---

  ### 📍 Exercise: Bar plots
  
  ```python
  # Create a bar plot of interest in math, separated by gender
  sns.catplot(x="Gender",
              y="Interested in Math",
              data=survey_data,
              kind="bar")
  ```
  <left>
    <img src="math.JPG" alt="math" width="300">
  </left>

  💡 Based on the bar plots, we can observe that:
  
  - *When the y-variable is Boolean (True/False), Seaborn's bar plot displays the proportion of responses that are True.*
  - *In this case, the plot shows that males report a significantly higher interest in math compared to females.*

---

  ### 📍 Exercise: Customizing Bar plots
  
  ```python
  # List of categories from lowest to highest
  category_order = ["<2 hours", "2 to 5 hours", "5 to 10 hours", ">10 hours"]

  # Turn off the confidence intervals
  sns.catplot(x="study_time",
              y="G3",
              data=student_data,
              kind="bar",
              order=category_order,
              ci=None)
  ```
  <left>
    <img src="study_time.JPG" alt="math" width="300">
  </left>

  💡 Based on the bar plots, we can observe that:
  
  - *The bar plot shows that students who reported studying more tend to have slightly higher average final grades.*
  - *However, the relationship between study time and performance is weak, indicating that study time alone may not strongly predict final grades.*

---
---

## 📦 2) Box plots

- Shows the **Distribution** of quantitative data
- See median, spread, skewness, and outliers
- Facilitates comparisons between groups

<div align="left">
  <img src="box_plot.JPG" width="350">
</div>

💡 Keypoint:

- colored box = represents 25th to 75th percentile
- line in middle of box = median
- whiskers( lines that extend from the ends of the box to show the range of the data, excluding outliers) = spread of distribution
- floating points = outliers

### 📍 Creating a box plots

```python
import matplotlib.pyplot as plt
import seaborn as sns

g = sns.catplot(x="time",
              y="total_bill",
              data=tips,
              kind="box"
              order=["Dinner","Lunch"])

plt.show()
```
<div align="left">
  <img src="box_plot2.JPG" width="300">
</div>

### 📍 Omitting the outliers from box plot
```python
g = sns.catplot(x="time",
              y="total_bill",
              data=tips,
              kind="box"
              sym="") 
```
<div align="left">
  <img src="omit_out.JPG" width="300">
</div>

### 📍 Changing whiskers using `whis`

```python
#by default, whiskers extend to 1.5 x (IQR)
#IQR = interquartile range (25th to 75th percentile of a distribution of data

#we can set this range as per our query

whis = 2.0 #for example, to extend to 2.0 x (IQR)
whis = [5,95] #to show 5th & 95th percentile
whis = [0,100] #to show min & max values
```
  ### 📍 Example: using `whis` for min & max values

  ```python
  g= sns.catplot(x="time",
                  y="total_bill",
                  data=tips,
                  kind="box",
                  whis=[0, 100])
  ```
  <div align="left">
    <img src="min_max.JPG" width="300">
  </div>
  
  💡 *Based on the box plot here, there's no outlier shown. This is because the box & whiskers cover the entire range of data*

---

### 📍 Exercise 1 : Creating & interpret a box plot

```python
# Specify the category ordering
study_time_order = ["<2 hours", 
                    "2 to 5 hours", 
                    "5 to 10 hours", 
                    ">10 hours"]

# Create a box plot and set the order of the categories
sns.catplot(x = "study_time",
            y = "G3",
            data=student_data,
            kind="box",
            order=study_time_order)
```
<div align="left">
  <img src="box_plotstudy.JPG" width="300">
</div>

### 📍 Exercise 2 : compare the distribution students based on internet access

```python
# Create a box plot with subgroups and omit the outliers
sns.catplot(x="internet",
              y="G3",
              data=student_data,
              kind="box",
              hue="location",
              sym="")

# Show plot
plt.show()
```
<div align="left">
  <img src="hue_urbanvsrural.JPG" width="300">
</div>

💡 *The median grades are quite similar between each group, but the spread of the distribution looks larger among students who have internet access.*

### 📍 Exercise 3 : Creating & interpret a box plot

```python
# Set the whiskers at the min and max values
sns.catplot(x="romantic", y="G3",
            data=student_data,
            kind="box",
            whis=[0, 100])

```
<div align="left">
  <img src="romantic.JPG" width="300">
</div>

💡 *The median grade is equal for both groups, but students not in a romantic relationship have a slightly higher maximum grade.*

---
---

## 🎯 3) Point plots

- Shows the **Mean** of quantitative variable
- Vertical line shows 95% confident intervals

### 📈 Difference between Point plots vs. line plots

<div align="center">
  <img src="line_point.JPG" width="500">
</div> <div align="center">
  
|              | Line Plot                   | Point Plot  |
| ------------ | --------------------------- | ----------- |
| X-axis type  | Quantitative (usually time) | Categorical |
| Shows mean   | ✅                           | ✅           |
| 95% CI shown | ✅                           | ✅           |
</div>

### 📊 Difference between Point plots vs. bar plots

<div align="center">
  <img src="point_bar.JPG" width="500">
</div> <div align="center">

|              | Bar Plot             | Point Plot           |
| ------------ | -------------------- | -------------------- |
| Visual style | Bars with error bars | Dots with error bars |
| Shows mean   | ✅                    | ✅                    |
| 95% CI shown | ✅                    | ✅                    |
</div>

### 📍 Example: Create a point plot

```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.catplot(x="age",
            y="masculinity_important",
            data=masculinity_data,
            hue="feel_masculine",
            kind="point")
plt.show()

```
<left>
  <img src="masculine_point.JPG" width="350">
</left>

### 📍 Example: Disconnect the point from the point plot

```python
sns.catplot(x="age",
            y="masculinity_important",
            data=masculinity_data,
            hue="feel_masculine",
            kind="point",
            join=False)
```
<left>
  <img src="join_off.JPG" width="350">
</left>

### 📍 Example: Display the median

```python
import matplotlib.pyplot as plt
import seaborn as sns
from numpy import median

sns.catplot(x="smoker",
            y="total_bill",
            data=tips,
            kind="point",
            estimator=median)
```
<left>
  <img src="median.JPG" width="350">
</left>

🔑 Keypoints:
- To use the median instead of the mean in plots, import median and pass it to the estimator parameter.
- This is useful when the dataset contains many outliers, as the mean can be skewed.
- The median is a more robust statistic in such cases.

### 📍 Example: Customize the confidence interval CI

```python
sns.catplot(x="smoker",
            y="total_bill",
            data=tips,
            kind="point",
            capsize=0.2) #to turn off the CI, use ci = None
```
For capsize = 0.2,

<left>
  <img src="capsize.JPG" width="350">
</left>

For ci = None,

<left>
  <img src="cioff.JPG" width="350">
</left>

---

### 📍 Exercise: Is being in a romantic relationship affect the school attendance?

```python
# Import median function from numpy
from numpy import median

# Plot the median number of absences instead of the mean
sns.catplot(x="romantic", y="absences",
			data=student_data,
            kind="point",
            hue="school",
            ci=None,
            estimator=median)

# Show plot
plt.show()
```
<left>
  <img src="romantic_point.JPG" width="350">
</left>

🔑 Keypoints:
- *Students in romantic relationships at the GP school show higher average and median absences, whereas this trend isn’t seen among students at the MS school.*













