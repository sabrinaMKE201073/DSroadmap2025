#### What is Pandas?
- Python lib for Data Analysis
- easily read dataset from csv, txt & other type of files
- when reading dataset with pandas, it will create DataFrame objects

#### 📍 working with DataFrame example (read csv file)
```python
import pandas as pd
df = pd.read_csv("masculinity.csv")
df.head()
```
<left>
  <img src="read_csv_example.JPG" alt="read csv example" width="370">
</left>

#### 📍 Using DataFrame with countplot()
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("masculinity.csv")
sns.countplot(x="how_masculine",
plt.show()
data=df)
```
<left>
  <img src="howmasculine_surveydata.JPG" alt="bar chart of how masculine dog data" width="370">
</left>
