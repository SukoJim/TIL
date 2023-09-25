# Basic OpenCV Syntax in Python

## Importing OpenCV and Basic Commands
```python
import cv2

# Read an image file
image = cv2.imread('image.jpg')

# Display the image
cv2.imshow('Image', image)

# Wait for a key press (Press any key to close the window)
cv2.waitKey(0)

# Close all windows
cv2.destroyAllWindows()
```


#### Saving an Image

This code demonstrates how to save an image as a new file.

```python
import cv2

# Read an image file
image = cv2.imread('image.jpg')

# Save the image as a new file
cv2.imwrite('saved_image.jpg', image)

```

#### Checking Image Size and Channels

This code shows how to check the size and number of channels in an image.

```python
import cv2

# Read an image file
image = cv2.imread('image.jpg')

# Check image dimensions
height, width, channels = image.shape
print(f'Height: {height}, Width: {width}, Channels: {channels}')

```

#### Cropping an Image

This code demonstrates how to crop a specific region of an image.

```python
import cv2

# Read an image file
image = cv2.imread('image.jpg')

# Crop a specific region of the image (starting from x, y coordinates and with a specific width and height)
x, y, width, height = 100, 50, 200, 150
cropped_image = image[y:y+height, x:x+width]

# Display the cropped image
cv2.imshow('Cropped Image', cropped_image)
cv2.waitKey(0)
cv2.destroyAllWindows()

```


#### Rotating an Image

This code shows how to rotate an image.

```python
import cv2

# Read an image file
image = cv2.imread('image.jpg')

# Set the rotation center and angle
center = (width // 2, height // 2)
angle = 45  # Rotate 45 degrees clockwise

# Create a rotation matrix
rotation_matrix = cv2.getRotationMatrix2D(center, angle, 1.0)

# Rotate the image
rotated_image = cv2.warpAffine(image, rotation_matrix, (width, height))

# Display the rotated image
cv2.imshow('Rotated Image', rotated_image)
cv2.waitKey(0)
cv2.destroyAllWindows()

```
