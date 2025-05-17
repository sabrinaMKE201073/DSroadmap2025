# SEABORN EXERCISES

### 📍 🎨📦Exercise 1: Customizing with a Color Palette
> - We want to understand the age distribution between male and female survey respondents by using a box plot. We'll also apply a custom color palette to make the plot more visually appealing.

```python
# Set the background style
sns.set_style("darkgrid")

# Use a custom color palette for gender
custom_palette = ["#39A7D0","#36ADA4"]
sns.set_palette(custom_palette)

# Create a box plot to compare age by gender
sns.catplot(x="Gender", y="Age", 
            data=survey_data, kind="box")

# Display the plot
plt.show()
```
<left>
  <img src="customized1.JPG" width="350">
</left>

🔑 Based om the plots:
- The median age is similar for both genders.
- However, females tend to be younger, with their ages more concentrated in the lower range compared to males.
- This gives us a basic snapshot of the age and gender breakdown in the survey responses.


