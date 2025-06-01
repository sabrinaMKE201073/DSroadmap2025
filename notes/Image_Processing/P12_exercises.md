# 🖼️ PART 1 : Image Processing Exercises with scikit-image

### 🌀 Exercise 1: Flip it!

<img src="e11.JPG" width="300">

```python
# Flip the image vertically
seville_vertical_flip = np.flipud(flipped_seville)

# Flip the image horizontally
seville_horizontal_flip = np.fliplr(seville_vertical_flip)

# Show the resulting image
show_image(seville_horizontal_flip, 'Seville')
```
<p align="center">
  <img src="e12.JPG" width="500">
</p>


---

### 📊 Exercise 2: Red Hot Histogram

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
<p align="center">
  <img src="e21.JPG" width="400">
</p>

📌 *This histogram shows a warm reddish tone—most pixels range between 0–150.*

---

### 🌓 Exercise 3: Go Binary with Global Threshold

<img src="e31.JPG" width="300">

```python
# Import the otsu threshold function
from skimage.filters import threshold_otsu

# Make the image grayscale using rgb2gray
chess_pieces_image_gray = rgb2gray(chess_pieces_image)

# Obtain the optimal threshold value with otsu
thresh = threshold_otsu(chess_pieces_image_gray)

# Apply thresholding to the image
binary = chess_pieces_image_gray > thresh

# Show the image
show_image(binary, 'Binary image')
```
<p align="center">
  <img src="e32.JPG" width="400">
</p>

---

### 🌗 Exercise 4: Uneven Background? Try Local Threshold

<img src="e41.JPG" width="300">

```python
global_thresh = threshold_otsu(page_image)

# Obtain the binary image by applying global thresholding
binary_global = page_image > global_thresh

# Show the binary image obtained
show_image(binary_global, 'Global thresholding')
```
<p align="center">
  <img src="e42.JPG" width="400">
</p>

📌 *Global thresholding can miss some text when the background isn't uniform.*

```python
# Import the local threshold function
from skimage.filters import threshold_local

# Set the block size to 35
block_size = 35

# Obtain the optimal local thresholding
local_thresh = threshold_local(page_image, block_size, offset=10)

# Obtain the binary image by applying local thresholding
binary_local = page_image > local_thresh

# Show the binary image
show_image(binary_local, 'Local thresholding')
```
<p align="right">
  <img src="e43.JPG" width="400">
</p>

📌 *Local thresholding shines when dealing with varied lighting.*

---


### 🧪 Exercise 5: Test All Thresholds!

<img src="e51.JPG" width="300">

```python
# Import the try all function
from skimage.filters import try_all_threshold

# Import the rgb to gray convertor function 
from skimage.color import rgb2gray

# Turn the fruits_image to grayscale
grayscale = rgb2gray(fruits_image)

# Use the try all method on the resulting grayscale image
fig, ax = try_all_threshold(grayscale, verbose=False)

# Show the resulting plots
plt.show()
```
<p align="center">
  <img src="e52.JPG" width="400">
</p>

📌 From all of the above thresholding method, this image works good with some global thresholding methods (like the "Yen" and "Mean") and not so well in others, (like the "Minimum").

---

### 🛠️ Exercise 6: Binarize Those Tools

<img src="e61.JPG" width="400">

```python
# Import threshold and gray convertor functions
from skimage.filters import threshold_otsu
from skimage.color import rgb2gray

# Turn the image grayscale
gray_tools_image = rgb2gray(tools_image)

# Obtain the optimal thresh
thresh = threshold_otsu(gray_tools_image)

# Obtain the binary image by applying thresholding
binary_image = gray_tools_image > thresh

# Show the resulting binary image
show_image(binary_image, 'Binarized image')
```

<p align="center">
  <img src="e62.JPG" width="400">
</p>

# 🖼️ PART 2 : Filters, Contrast, Transformation and Morphology

### Exercise 1: Edge detection

<img src="ex1.JPG" width="400">

```python
# Import the color module
from skimage import color

# Import the filters module and sobel function
from skimage.filters import sobel

# Make the image grayscale
soaps_image_gray = color.rgb2gray(soaps_image)

# Apply edge detection filter
edge_sobel = sobel(soaps_image_gray)

# Show original and resulting image to compare
show_image(soaps_image, "Original")
show_image(edge_sobel, "Edges with Sobel")
```

<p align="center">
  <img src="ex12.JPG" width="400">
</p>

📌 The edges of all the figures in the scene are highlighted.

### Exercise 2: Using Gaussian filter (to reduce noise)

<img src="building_image.JPG" width="200">

```python
# Import Gaussian filter 
from skimage.filters import gaussian

# Apply filter
gaussian_image = gaussian(building_image, multichannel=True)

# Show original and resulting image to compare
show_image(building_image, "Original")
show_image(gaussian_image, "Reduced sharpness Gaussian")
```

<p align="center">
  <img src="building_image_outtputt.JPG" width="400">
</p>

---

### Exercise 3: Contrast on chest x-ray

<img src="xray_in.JPG" width="200">

```python
# Import the required module
from skimage import exposure

# Show original x-ray image and its histogram
show_image(chest_xray_image, 'Original x-ray')

plt.title('Histogram of image')
plt.hist(chest_xray_image.ravel(), bins=256)
plt.show()

# Use histogram equalization to improve the contrast
xray_image_eq =  exposure.equalize_hist(chest_xray_image)

# Show the resulting image
show_image(xray_image_eq, 'Resulting image')
```

<p align="center">
  <img src="xray_res.JPG" width="300">
</p>

---

### Exercise 4: Contrast on aerial places 

<img src="aerial1.JPG" width="200">

```python
from skimage import exposure
image_eq =  exposure.equalize_adapthist(image_aerial,clip_limit=0.03)
show_image(image_aerial, 'Original')
show_image(image_eq, 'Resulting image')
```

<p align="center">
  <img src="adap2.JPG" width="300">
</p>

---

### Exercise 5: Contrast on cup of tea 

<img src="cup1.JPG" width="200">

```python
from skimage import data, exposure

original_image = data.coffee()
adapthist_eq_image = exposure.equalize_adapthist(original_image,clip_limit=0.03)

show_image(original_image)
show_image(adapthist_eq_image, '#ImageProcessingDatacamp')
```

<p align="center">
  <img src="cup2.JPG" width="300">
</p>


---

### Exercise 6: Aliasing, rotating and rescaling of a cat

<img src="cat1.JPG" width="200">

```python
from skimage.transform import rotate, rescale

# Rotate the image 90 degrees clockwise 
rotated_cat_image = rotate(image_cat, -90)

# Rescale with anti aliasing
rescaled_with_aa = rescale(rotated_cat_image, 1/4, anti_aliasing=True, multichannel=True)

# Rescale without anti aliasing
rescaled_without_aa = rescale(rotated_cat_image, 1/4, anti_aliasing=False, multichannel=True)

show_image(rescaled_with_aa, "Transformed with anti aliasing")
show_image(rescaled_without_aa, "Transformed without anti aliasing")
```

<p align="center">
  <img src="cat2.JPG" width="400">
</p>

📌 Anti aliasing filter prevents the poor pixelation effect to happen, making it look better but also less sharp.

---

### Exercise 7: Enlarging images

```python
from skimage.transform import rescale
from skimage import data

rocket_image = data.rocket()
enlarged_rocket_image = rescale(rocket_image,3,anti_aliasing=True, multichannel=True)

show_image(rocket_image)
show_image(enlarged_rocket_image, "3 times enlarged image")
```
<img src="rocket1.JPG" width="300">

<p align="center">
  <img src="rocket2.JPG" width="400">
</p>

📌 The image went from being 600 pixels wide to over 1700 and it still does not look poorly pixelated.

---

### Exercise 8: Proportionally resizing

```python
# Import the module and function
from skimage.transform import resize

# Set proportional height so its half its size
height = int(dogs_banner.shape[0] / 2)
width = int(dogs_banner.shape[1] / 2)

# Resize using the calculated proportional height and width
image_resized = resize(dogs_banner, (height, width),
                       anti_aliasing=True)

# Show the original and resized image
show_image(dogs_banner, 'Original')
show_image(image_resized, 'Resized image')
```

<img src="dog1.JPG" width="300">

<p align="center">
  <img src="dog2.JPG" width="300">
</p>

### Exercise 9: Morphology erosion on Handwritten letters

```python
# Import the morphology module
from skimage import morphology

# Obtain the eroded shape 
eroded_image_shape = morphology.binary_erosion(upper_r_image)
# See results
show_image(upper_r_image, 'Original')
show_image(eroded_image_shape, 'Eroded image')
```
<p align="center">
  <img src="letterR.JPG" width="300">
</p>
📌 Erosion is useful for removing minor white noise.

---

### Exercise 10: Morphology dilation on thresholded image

```python
from skimage import morphology

dilated_image = morphology.binary_dilation(world_image)

show_image(world_image, 'Original')
show_image(dilated_image, 'Dilated image')
```
<p align="center">
  <img src="map1.JPG" width="300">
</p>

<p align="center">
  <img src="map2.JPG" width="300">
</p>

📌 Dilation morphology method able to removed the noise of the segmented image and now it became more uniform.




