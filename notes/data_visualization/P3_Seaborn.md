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
    <img src="change_order.JPG" alt="order of masculinity example" width="300">
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
  # Create count plot of internet usage
  sns.catplot(x="Internet usage",
              data=survey_data,
              kind="count")

  # Rotate x-axis labels
  plt.xticks(rotation=45)

  # Show plot
  plt.show()
  ```
  <left>
    <img src="count_plotex.JPG" alt="survey on internet usage" width="300">
  </left>

  💡 *Based on the bar plot,we can see that most of young people spend few hours a day on the internet*
































