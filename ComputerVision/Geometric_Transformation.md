# Geometric Transformations on Images Using Affine Matrices

Geometric transformations using affine matrices are essential operations in computer vision and image processing. Affine matrices allow you to easily apply various transformations to images, including translation, rotation, flipping, and shearing. In this guide, we'll explain these transformations and provide code examples in Python.

## Translation

Translation is the process of moving an image in the x and y directions. The affine matrix for translation has the following form:

```
| 1 0 tx |   
| 0 1 ty |   
| 0 0 1  |
```

Here's a Python code example for applying a translation transformation to an image:

```python
import cv2
import numpy as np

# Load the image
image = cv2.imread('input.jpg')

# Define the translation matrix
tx = 50  # Move in the x-direction
ty = 30  # Move in the y-direction
translation_matrix = np.array([[1, 0, tx],
                               [0, 1, ty]])

# Apply the translation to the image
translated_image = cv2.warpAffine(image, translation_matrix, (image.shape[1], image.shape[0]))

# Save the resulting image
cv2.imwrite('translated_image.jpg', translated_image)
```

## Rotation
Rotation is the process of rotating an image by a specified angle. The affine matrix for rotation is as follows:
```
| cos(θ)  -sin(θ)  0 |
| sin(θ)   cos(θ)  0 |
|   0       0      1 |
```

Here's a Python code example for applying a rotation transformation to an image:
```python

# Set the rotation angle (e.g., 45 degrees)
angle = 45

# Calculate the rotation matrix
rotation_matrix = cv2.getRotationMatrix2D((image.shape[1] / 2, image.shape[0] / 2), angle, 1)

# Apply the rotation to the image
rotated_image = cv2.warpAffine(image, rotation_matrix, (image.shape[1], image.shape[0]))

# Save the resulting image
cv2.imwrite('rotated_image.jpg', rotated_image)
```

## Flipping
Flipping is the process of flipping an image horizontally or vertically. For example, for horizontal flipping, the affine matrix is as follows:
```
| -1  0  w |
|  0  1  0 |
|  0  0  1 |
```
Here's a Python code example for applying a horizontal flip transformation to an image:
```python

# Apply horizontal flipping
flipped_image = cv2.flip(image, 1)  # 1 represents horizontal flipping

# Save the resulting image
cv2.imwrite('flipped_image.jpg', flipped_image)

```

## Shearing
Shearing is the process of tilting an image in the x or y direction, causing a displacement. The affine matrix for shearing depends on the type of shearing. Here's an example of x-direction shearing:
```python

# Apply x-direction shearing
shearing_matrix = np.array([[1, 0.5, 0],
                            [0, 1, 0]])

# Apply shearing to the image
sheared_image = cv2.warpAffine(image, shearing_matrix, (image.shape[1], image.shape[0]))

# Save the resulting image
cv2.imwrite('sheared_image.jpg', sheared_image)
```
