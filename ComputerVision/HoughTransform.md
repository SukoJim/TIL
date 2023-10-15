# Hough Transform

## Concept
- **Polar Coordinate Representation**: Hough Transform represents lines in polar coordinates (rho, theta), where rho is the distance from the origin to the line and theta is the angle between the line and the origin.

- **Hough Space**: Hough Transform represents lines in the Hough space, also known as the accumulation space. In this space, each point (x, y) forms intersections for all possible lines, aiding in finding lines in the image.

- **Voting Process**: Edge pixels cast votes for all possible lines. This process generates potential candidates for lines within the image.

- **Accumulation of Votes**: Accumulation of votes from all edge pixels results in the (rho, theta) pairs with the highest votes representing actual lines in the image.

- **Thresholding**: Lines are extracted by considering (rho, theta) pairs with votes exceeding a certain threshold.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmZ3P8%2FbtqD8i2g0qU%2FtOaqetqEE6Onqge5abkTqk%2Fimg.png"/>   

## Hough Transform Process with Code

1. **Image Preprocessing**: Load the input image and perform preprocessing, such as converting it to grayscale and detecting edges. This is typically done using the Canny edge detector.
 >  ```python
 >  import cv2
 >  
 >  image = cv2.imread('smaple_image.jpg')
 >  gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
 >  edges = cv2.Canny(gray, 50, 150, apertureSize=3)
 >  ```
2. **Hough Transform**: Apply the Hough Transform using the `cv2.HoughLines()` function in OpenCV.
  > ```python
  > lines = cv2.HoughLines(edges, 1, np.pi / 180, threshold)
  > ```
  >- `edges` is the edge-detected image.
  >- `1` represents the resolution of rho in pixels.   
  >- `np.pi / 180` specifies the resolution of theta in radians.   
  >- `threshold` is the minimum number of votes required to consider a line.

3. **Iterate Over Detected Lines**: Loop through the detected lines and convert them from polar coordinates to Cartesian coordinates.
   ```python
   if lines is not None:
    for rho, theta in lines[:, 0]:
        a = np.cos(theta)
        b = np.sin(theta)
        x0 = a * rho
        y0 = b * rho
        x1 = int(x0 + 1000 * (-b))
        y1 = int(y0 + 1000 * (a))
        x2 = int(x0 - 1000 * (-b))
        y2 = int(y0 - 1000 * (a))
   ```

4. **Draw Lines on the Image**: Use the Cartesian coordinates to draw the detected lines on the original image.
   ```python
   cv2.line(image, (x1, y1), (x2, y2), (0, 0, 255), 2)
   ```


## Sample output Image:
<img src="https://i.stack.imgur.com/IG4CZ.png">
