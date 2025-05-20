## Visualizing relationships over time

Q1: Create a line plot showing the average number of kids a couple had during their marriage, arranged by the year that the couple got married.

```python
# Define the marriage_year column
divorce["marriage_year"] = divorce["marriage_date"].dt.year

# Create a line plot showing the average number of kids by year
sns.lineplot(data=divorce, x="marriage_year", y="num_kids")
plt.show()
```

<left>
  <img src="num_kids_year.JPG" width="450">
</left>

📌 it looks like couples who had later marriage years also had fewer children during their marriage.

---

