# Module 1: Getting to Know a Dataset

---

## 🧰 1. Functions for Exploring Data

| Function           | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `.head()`          | Returns the first few rows – useful for getting a quick overview.           |
| `.info()`          | Displays column names, non-null counts, and data types.                     |
| `.value_counts()`  | Shows counts of unique values – best used on categorical columns.           |
| `.describe()`      | Gives summary stats for numeric columns (mean, std, min, 25/50/75%, max).   |

---

## 📊 2. Visualizing Numerical Data

### Example: Plotting a Histogram with Seaborn

```Python
import seaborn as sns
import matplotlib.pyplot as plt
sns.histplot(data=books,
            x="rating",
            binwidth=.1)
plt.show()
```
  
  <left>
    <img src="hist1.JPG" width="350">
  </left>

---

## ✅ 3. Data Validation and Type Checking

### 🔍 Checking Data Types

```Python
books.dtypes
```

> Note: `.dtypes` may show a general type like `object` for strings or mixed types.

---

### 🔄 Converting Data Types using `.astype()`

```Python
books["year"] = books["year"].astype(int)
books.dtypes
```

  <left>
    <img src="float_to_int.JPG" width="150">
  </left>

### 🧮 Python Data Types Summary

| Type        | Python Name |
|-------------|--------------|
| String      | `str`        |
| Integer     | `int`        |
| Float       | `float`      |
| Dictionary  | `dict`       |
| List        | `list`       |
| Boolean     | `bool`       |

---

### 🏷️ 4. Validating categorical data 

Using `.isin()` to Check Specific Categories

```Python
books["genre"].isin(["Fiction", "Non Fiction"])
```

  <left>
    <img src="isin.JPG" width="200">
  </left>

> Tip: Use `~` to invert the result and filter items not in the list.

---

#### 🔎 Filter Rows Based on Category Match

 ```Python
 books[books["genre"].isin(["Fiction", "Non Fiction"])].head()
 ```

 <left>
    <img src="isin2.JPG" width="500">
  </left>

---

### 🧪 5. Validating numerical data 

Handy Functions:

- `df.select_dtypes("number")` - to select & view numerical columns in the dataframe

- `df["column"].min()`

- `df["column"].max()`


 #### 🔸 Visualize with `sns.boxplot` 

```Python
sns.boxplot(data=books, x="year", y="genre")
```

  <left>
    <img src="bocplot.JPG" width="350">
  </left>

> Observation: Children's books tend to be published slightly later, but year ranges across genres are similar.



























