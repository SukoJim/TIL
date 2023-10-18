# Harris Corner Detection

Harris Corner Detection is a method used in computer vision to find key features in an image. This method helps determine whether a specific pixel in an image is a corner or not, making it useful for feature extraction, object detection, object tracking, and various other applications.

## Concept

Harris Corner Detection is a technique that identifies points in the image where there is a significant change in brightness in all directions, making them suitable corner candidates. These corner points exhibit a strong response to shifts in any direction.

## Algorithm Flow

1. **Compute Image Gradients (Sobel Mask)**:
   - Calculate the gradients of the image to determine both the direction and magnitude of brightness changes. The Sobel mask is typically used for this purpose.

2. **Compute Squared Derivatives of Brightness Changes within a Window**:
   - Calculate the squared derivatives of brightness changes within a local window around each pixel. These squared derivatives represent the magnitude of brightness changes and are used to identify corner candidates.

3. **Compute Harris Response Function**:
   - Calculate the Harris Corner Response function, which takes into account the magnitude and direction of brightness changes. This response function helps in identifying corner features.

4. **Select Points with High Response Values**:
   - Pixels with response values higher than a certain threshold are considered corner candidates. Typically, a threshold is set to identify the significant corner points.

5. **Refine Corner Candidates (Non-Maximum Suppression)**:
   - To improve the accuracy of corner detection, non-maximum suppression is performed to eliminate redundant corner candidates and determine the exact corner locations.

## Using Custom Approach with Sobel Mask

  ```python
  import cv2
  import numpy as np
  
  # Load the image
  image = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)
  
  # Define Sobel masks
  sobel_x = np.array([[-1, 0, 1], [-2, 0, 2], [-1, 0, 1]])
  sobel_y = np.array([[-1, -2, -1], [0, 0, 0], [1, 2, 1]])
  
  # Apply Sobel filters
  gradient_x = cv2.filter2D(image, -1, sobel_x)
  gradient_y = cv2.filter2D(image, -1, sobel_y)
  
  # Calculate squared derivatives of brightness changes
  Ixx = gradient_x * gradient_x
  Iyy = gradient_y * gradient_y
  Ixy = gradient_x * gradient_y
  
  # Calculate the Harris response function
  k = 0.04  # Adjustable constant
  det = Ixx * Iyy - Ixy * Ixy
  trace = Ixx + Iyy
  harris_response = det - k * (trace ** 2)
  
  # Select points with high response values
  threshold = 0.01 * harris_response.max()
  corner_points = np.where(harris_response > threshold)
  
  # Visualize the result
  image[corner_points] = [0, 0, 255]  # Mark corners in red
  cv2.imshow('Harris Corners', image)
  ```
## Using Built-In Python OpenCV Function
  ```python
  import cv2
  
  # Load the image
  image = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)
  
  # Harris Corner Detection
  corners = cv2.cornerHarris(image, 2, 3, 0.04)  # 2: Sobel mask size, 3: Harris corner detection parameters, 0.04: Harris corner detection parameters
  
  # Select corner candidates
  threshold = 0.01 * corners.max()
  corner_points = (corners > threshold).nonzero()
  
  # Visualize the result
  image[corner_points] = [0, 0, 255]  # Mark corners in red
  cv2.imshow('Harris Corners', image)
  cv2.waitKey(0)
  cv2.destroyAllWindows()
  ```
### `cv2.cornerHarris` Function

  **Parameters:**
  >- `src` (input image): Input image. **In the custom approach, it corresponds to the image loaded and processed as 'image.'**
  >- `blockSize`: Size of the neighborhood for each corner detection. It relates to setting the window size in the custom approach.
  >- `ksize`: Aperture parameter for the Sobel operator, specifying the size of the Sobel kernel. It is related to defining the size of Sobel masks in the custom approach.
  >- `k`: Harris detection parameter, where an effective value is typically 0.04. It's used for computing the Harris response function in the custom approach.
  
  **Returns:**
  >- `dst`: Harris corner response map. It represents the responses of corner candidate points.
  
  **Additional Parameters (Custom Approach):**
  >- `threshold`: Threshold for response values. It's used in the custom approach to select corner candidates with response values higher than the threshold.
  >- `corner_points`: Array for storing corner candidates with response values exceeding the threshold. In the custom approach, it is used to save the corner candidates after applying the threshold to the response values.
