## Exercise 1: Variance and standard deviation

a) Question: Calculate the variance and standard deviation of co2_emission for each food_category with the .groupby() and .agg() methods 

```python
print(food_consumption.groupby('food_category')['co2_emission'].agg(['var','std']))
```

<left>
  <img src="ex1.JPG" width="250">
</left>

b) Question: Create a histogram of co2_emission for the beef in food_category and show the plot.

```python
# Create histogram of co2_emission for food_category 'beef'
food_consumption[food_consumption['food_category'] == 'beef']['co2_emission'].hist()

plt.xlabel('CO2 Emissions (kg CO2 per person per year)')
plt.ylabel('Frequency')
plt.title('Distribution of CO2 Emissions for Beef')

plt.show()
```

<left>
  <img src="ex1b.JPG" width="400">
</left>
