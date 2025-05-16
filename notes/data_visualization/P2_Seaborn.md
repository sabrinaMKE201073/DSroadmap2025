Relation plot & subplot
1) relplot()
   - is a relational plot (either scatter/line plot)
   - lets you create subplots in a single figure

---

### Subplots in column example
  
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

### Subplots in row example
  
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


2) 
