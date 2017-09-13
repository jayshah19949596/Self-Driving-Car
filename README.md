## Project: **Finding Lane Lines on the Road** 
***

This project is written in python3 and uses OpenCv for applying computer vision

## **My PipeLine Approach** 
***
### My pipeline includes the following steps
1. Read the image and convert it to Grey Scale
2. Apply Gaussian Filter to grey scale image
3. Apply Canny Edge Detection to gaussian image
4. Find Region of Interest in the image
5. Apply hough lines to detect lines 
6. Average/extrapolate the lines to draw lane lines
7. Overlay two images

![alt text](https://github.com/jayshah19949596/Lane-Detection/blob/master/Images/Grey.PNG")

## Step 1: **Reading the image and  convert it to Grey Scale** 
*** 
- Used matplotlib to read the image  `mpimg.imread('test.jpg')` 
- Used OpenCv to conver the read image to grey scale by `cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)`
- The result is in the below image :

## Step 2: **Apply Gaussian Filter** 
*** 
- Used OpenCV to apply gaussian filter.
- `cv2.GaussianBlur(img, (kernel_size, kernel_size), 0)`
- `kernel_size` is the size of the filter to be applied on the grey scale image.
- The gaussian filter smoothens the image and results in a blur image.
- The result is in the below image :
![alt text](https://github.com/jayshah19949596/Lane-Detection/blob/master/Images/Gaussian.PNG")

## Step 3: **Apply Canny Edge Detection ** 
*** 
- Used OpenCV to apply Canny edge.
- `cv2.Canny(img, low_threshold, high_threshold)`
- `low_threshold` : All the pixel values below the `low_threshold` value will be removed.
- `high_threshold`: All the pixel values above the `high_threshold` value are kept.
- The pixel Values in between the `low_threshold` and `high_threshold` is only kept if they are connected to a pixel above the `high_threshold`.
- The edged image is shown below :
![alt text](https://github.com/jayshah19949596/Lane-Detection/blob/master/Images/Canny.PNG")

## Step 4: **Find Region of Interest ** 
*** 
- Used OpenCV to find region of interest.
- `cv2.fillPoly(mask, vertices, ignore_mask_color)`
- `vertices` : Numpy array with vertices of polygon to be redrawn.
- The result image is below :

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

- `cv2.bitwise_and()` for eleminating all the edges outside the region of interest .
- So now the edges in the image is only inside the region of interest.
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")


## Step 5: **Detect Lines ** 
*** 
- Used OpenCV to detect line.
- The technique used is called Hough lines
- `cv2.HoughLinesP(img, rho, theta, threshold, np.array([]), minLineLength=min_line_len, maxLineGap=max_line_gap)`
- `rho` : distance resolution in pixels of the Hough grid
- `theta` : angular resolution in radians of the Hough grid
- `threshold` : minimum number of votes (intersections in Hough grid cell)
- `min_line_length` : minimum number of pixels making up a line
- `max_line_gap` : maximum gap in pixels between connectable line segments
- Hough space is a parametric space
- A line in real world is a single point in hough space
- A point in real world is a line in hough space
- The point in hough space where lines meet more then a threshold that point is considered to be a line in real world
- The result of lines detected by hough transformation is shown below:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

