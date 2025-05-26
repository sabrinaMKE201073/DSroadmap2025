## Exercise 1: Variance and standard deviation

Question: Calculate the variance and standard deviation of co2_emission for each food_category with the .groupby() and .agg() methods 

```python
print(food_consumption.groupby('food_category')['co2_emission'].agg(['var','std']))
```

<left>
  <img src="ex1.JPG" width="250">
</left>
