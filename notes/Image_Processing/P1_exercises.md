### Exercise 1: Flipping out

<img src="e11.JPG" width="300">

```python
# Flip the image vertically
seville_vertical_flip = np.flipud(flipped_seville)

# Flip the image horizontally
seville_horizontal_flip = np.fliplr(seville_vertical_flip)

# Show the resulting image
show_image(seville_horizontal_flip, 'Seville')
```
<p align="right">
  <img src="e12.JPG" width="500">
</p>


---

### Exercise 2: Histograms

<img src="e22.JPG" width="300">

```python
# Obtain the red channel
red_channel = image[:, :, 0]

# Plot the red histogram with bins in a range of 256
plt.hist(red_channel.ravel(), bins=256)

# Set title and show
plt.title('Red Histogram')
plt.show()
```
<p align="right">
  <img src="e21.JPG" width="500">
</p>
