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
































2) 
