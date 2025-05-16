Relation plot & subplot
1) relplot()
   - is a relational plot (either scatter/line plot)
   - lets you create subplots in a single figure

---

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




2) 
