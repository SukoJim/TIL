# Edge Detection
**Edge Detection** is one of the computer vision tasks aimed at identifying the boundaries of objects in an image. Edge detection is crucial in image processing and object recognition. In this context, we will explain two major edge detection techniques: "Sobel Mask" and "Canny Edge Detection."

## Sobel Mask
**Sobel Mask** is one of the filters commonly used for edge detection. This mask calculates the derivatives in an image to detect edges.

### How it works
The **Sobel mask** convolves an image with two kernels, one for the horizontal and one for the vertical direction. These kernels play a role in calculating the edges in both the horizontal and vertical directions. After obtaining horizontal and vertical gradient images, the edge strength is computed. This edge strength represents the location of the edges.

**Horizontal Sobel Filter (Sobel X):**
>[-1 0 1]     
>[-2 0 2]   
>[-1 0 1]

**Vertical Sobel Filter (Sobel Y):**
>[-1 -2 -1]     
>[ 0 0 0]   
>[ 1 2 1]

### Implementation
>1. Convert the image to grayscale.
>2. Define Sobel masks for the horizontal and vertical directions.
>3. Convolve the image with each mask to obtain horizontal and vertical gradient images.
>4. Calculate edge strength using the gradient images.
>5. Detect edges using the edge strength.


### Sobel Mask Implementation Example (Python Code)
```python
import cv2
import numpy as np

# Read the image in grayscale.
image = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)

# Define Sobel masks for the horizontal and vertical directions.
sobel_x = np.array([[-1, 0, 1], [-2, 0, 2], [-1, 0, 1]])
sobel_y = np.array([[-1, -2, -1], [0, 0, 0], [1, 2, 1]])

# Calculate horizontal and vertical derivatives.
gradient_x = cv2.filter2D(image, -1, sobel_x)
gradient_y = cv2.filter2D(image, -1, sobel_y)

# Calculate edge strength.
magnitude = np.sqrt(gradient_x**2 + gradient_y**2)

# Save edge strength as an image.
cv2.imwrite('sobel_output.jpg', magnitude)
```


## Canny Edge Detection
**Canny Edge Detection** is an advanced technique for detecting edges in an image. The Canny algorithm consists of several steps and effectively performs noise reduction and accurate edge detection.

### How it works and Steps
>1. Gaussian Smoothing: The image is first blurred using a Gaussian filter to reduce noise.
>2. Sobel Filtering: Horizontal and vertical Sobel filters are applied to calculate edge gradients.
>3. Edge Strength and Direction Calculation: Edge strength and direction are computed based on the gradients at each pixel.
>4. Edge Detection: Edges are detected using edge strength.
>5. Edge Tracking by Hysteresis: Weak edge pixels detected with a lower threshold are connected to strong edges to form complete edges. This step enhances edge continuity.
>6. Canny Edge Detection employs these steps to accurately detect edges while minimizing noise.

### Canny Edge Detection Implementation Example (Python Code)
```python
import cv2
import numpy as np

# Read the image in grayscale.
image = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)

# Gaussian smoothing to reduce noise.
blurred = cv2.GaussianBlur(image, (5, 5), 0)

# Calculate gradients using Sobel filters in both directions.
gradient_x = cv2.Sobel(blurred, cv2.CV_64F, 1, 0, ksize=3)
gradient_y = cv2.Sobel(blurred, cv2.CV_64F, 0, 1, ksize=3)

# Calculate edge strength and direction.
magnitude = cv2.magnitude(gradient_x, gradient_y)
direction = cv2.phase(gradient_x, gradient_y, angleInDegrees=True)

# Perform edge detection using Canny with threshold values.
edges = cv2.Canny(image, threshold1=30, threshold2=100)

# Save the Canny edge output as an image.
cv2.imwrite('canny_output.jpg', edges)

```
