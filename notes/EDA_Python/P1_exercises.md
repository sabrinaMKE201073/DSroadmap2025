### 🔹 Exercise 1
```python
# Import the required visualization libraries
import seaborn as sns
import matplotlib.pyplot as plt

# Create a histogram of 2021 unemployment; show a full percent in each bin
sns.histplot(data=unemployment,
            x="2021",
            binwidth=1.0)
plt.show()
```

<left>
  <img src="unemployment in 2021.JPG" width="350">
</left>

📌 It looks like 2021 unemployment hovered around 3% to 8% for most countries in the dataset, but a few countries experienced very high unemployment of 20% to 35%.

---

### 🔹 Exercise 2

