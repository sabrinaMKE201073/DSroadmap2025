Relation plot & subplot
1) relplot()
   - is a relational plot (either scatter/line plot)
   - lets you create subplots in a single figure

---

### Subplots 1 : column example
  
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

### Subplots 2 : row example
  
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

### Subplots 3: combination of column and row example
  
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

### Subplots 4: setting how many subplots per row & column order
  
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

### Exercise : Creating two-factor subplots
  
```python
sns.relplot(x="G1", y="G3", 
            data=student_data,
            kind="scatter", 
            col="schoolsup",
            col_order=["yes", "no"],
            row = "famsup",
            row_order=["yes", "no"] 
            )
```
<left>
  <img src="two_factors.JPG" alt="creating two factor subplots" width="300">
</left>
📌 From the subplots, The first semester grade does correlate with the final grade, regardless of what kind of support the student received.

---

2) Customizing Scatter plots (size,hue,style,alpha)
- better contrast
- easier to analyse the plots

### Exercise 1 : relationship between power of car's engine vs fuel efficiency
  
```python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create scatter plot of horsepower vs. mpg
sns.relplot(x="horsepower", y="mpg", 
            data=mpg, kind="scatter", 
            size="cylinders",
            hue="cylinders")

# Show plot
plt.show()
```
<left>
  <img src="horsepower_plot.JPG" alt="vary the color of points by no. of cylinder" width="400">
</left>
📌 Cars with higher horsepower tend to get a lower number of miles per gallon. They also tend to have a higher number of cylinders. 

### Exercise 2 : relationship between how fast a car can accelerate at different country
  
```python
# Create a scatter plot of acceleration vs. mpg
sns.relplot(x="acceleration", y="mpg", 
            data=mpg, kind="scatter",
            hue="origin",
            style="origin")
```
<left>
  <img src="acceleration_country.JPG" alt="how fast a car can accelerate at different country" width="400">
</left>
📌 Cars from the USA tend to accelerate more quickly and get lower miles per gallon compared to cars from Europe and Japan.







 
