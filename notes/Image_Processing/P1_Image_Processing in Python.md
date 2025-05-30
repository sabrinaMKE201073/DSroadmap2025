<img src="scikitimage.JPG" width="200">

## What is image processing?
> subset of computer vision

Operations to on images and videos to:
- Enhance an image
- Extract useful information
- Analyze it and make decisions

<img src="Image1.JPG" width="350">

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

<img src="imagee.JPG" width="500">

<img src="grayscale.JPG" width="500">

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







