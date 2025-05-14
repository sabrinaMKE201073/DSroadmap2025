# 🧠 Topic: Introduction to Statistics in Python

## 🎯 Learning Objectives
- [ ] Understand and compute basic summary statistics in Python
- [ ] Use NumPy functions for statistical analysis
- [ ] Apply statistical concepts to analyze datasets
---
### ✅ Concept 1: Summary Statistics

---

### 🔷 1️⃣ Variance

- Measures how spread out the data points are from the **mean**.
- By default, `np.var()` calculates **population variance**.
- Use `ddof=1` to calculate **sample variance** instead.

🧪 **Code Example**
```python
import numpy as np

# Sample variance of 'sleep_total' column
np.var(msleep['sleep_total'], ddof=1)
```
🔎 Note: Without ddof=1, you're computing population variance.

### 🔷 2️⃣ Standard Deviation

#### Option 1: Manually take the square root of the variance
```python
np.sqrt(np.var(msleep['sleep_total'], ddof=1))
```
#### Option 2: Use np.std directly
```python
np.std(msleep['sleep_total'], ddof=1)
```

---

### ✅ Concept 2: Random Numbers and Probability
-- details

### ✅ Concept 3: More Distributions and the Central Limit Theorem
-- details

### ✅ Concept 4: Correlation and Experimental Design
-- details
