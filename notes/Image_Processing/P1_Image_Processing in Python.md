<img src="scikitimage.JPG" width="200">

## What is image processing?
> subset of computer vision

Operations to on images and videos to:
- Enhance an image
- Extract useful information
- Analyze it and make decisions

<img src="Image1.JPG" width="300">

### Purposes

1) Visualization
> Objects that are not visible

2) Image sharpening and restoration
> A better image

3) Image retrieval
> Seek for the image of interest
      
4) Measurement of pattern
> Measures various objects

5) Image Recognition
> Distinguish objects in an image

---

## What is an image?
A digital image is an array/matrix/square pixels which arranged in columns & rows (2-dimensional matrix)

<img src="imagee.JPG" width="400">

<img src="grayscale.JPG" width="400">

--- 

## Import image for scikit-image

```python
from skimage import data
rocket_image = data.rocket()
```
<img src="skimage1.JPG" width="300">

## RGB vs Grayscale color

```python
from skimage import color
grayscale = color.rgb2gray(original)
rgb = color.gray2rgb(grayscale)
```
<img src="gray1.JPG" width="300">

```python
#using matplotlib function to show image
show_image(grayscale, "Grayscale")
```
<img src="gray2.JPG" width="200">

---

### Exercise: RGB to grayscale

```python
# Import the modules from skimage
from skimage import data, color

# Load the rocket image
rocket = data.rocket()

# Convert the image to grayscale
gray_scaled_rocket = color.rgb2gray(rocket)

# Show the original image
show_image(rocket, 'Original RGB image')

# Show the grayscale image
show_image(gray_scaled_rocket, 'Grayscale image')
```

<img src="original1.JPG" width="200">
<img src="or2gray.JPG" width="200">


