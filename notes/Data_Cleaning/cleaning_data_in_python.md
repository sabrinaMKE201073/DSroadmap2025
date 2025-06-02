## Finding inconsistent categories
> data that are needed to be dropped

```python
# Find the cleanliness category in airlines not in categories
cat_clean = set(airlines['cleanliness']).difference(categories['cleanliness'])

# Find rows with that category
cat_clean_rows = airlines['cleanliness'].isin(cat_clean)

# Print rows with inconsistent category
print(airlines[cat_clean_rows])
```

<img src="1a.JPG" width="700">


```python
# Print rows with consistent categories only
print(airlines[~cat_clean_rows])
```

<img src="1b.JPG" width="700">
