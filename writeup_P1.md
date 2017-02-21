
#**Finding Lane Lines on the Road** 

##Writeup for Self-Driving Car Engineer Nanodegree Project 1: Finding Lane Lines on the Road


---

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Original"
[image2]: ./output_images/solidWhiteCurve_gray.jpg "Grayscale"
[image3]: ./output_images/solidWhiteCurve_blur_gray.jpg "Gaussian"
[image4]: ./output_images/solidWhiteCurve_masked_edges.jpg "Canny"
[image5]: ./output_images/solidWhiteCurve_masked_hough.jpg "Hough"
[image6]: ./output_images/solidWhiteCurve_final_image.jpg "Final"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

####My pipeline consists of 5 steps starting from the original image:
![alt text][image1]
####1. Convert image to grayscale
![alt text][image2]
####2. Apply Gaussian Blur
![alt text][image3]
####3. Apply Canny Edge Detection and apply mask (area of interest) to the image 
![alt text][image4]
####4. Calculate Hough lines of the masked Canny edge picture 
![alt text][image5]
####5. Create two averaged and extrapolated lines
  * Categorize points according to slope and position into left and right line point cloud
  * Use linear regression to fit a line through each point cloud (calculate coefficients)
  * Calculate end points in region of interest and draw lines into picture

![alt text][image6]

###2. Possible shortcomings of the current pipeline
####1. Shadows, edges, cars and other lines will be detected and interpreted
####2. Colors are not used for detection and lines in grayscale can be hard to detect (depending on lighting etc)
####3. No backup system (other sensors) in case of bad visibility
####4. No algorithm for strech where no lines are detected
####5. Situation where multiple lines are very close (e.g. construction zone) has not been considered
####6. Tight turns and intersections have not been considered yet
####7. Parking situation has not been implemented yet
####8. Driving at night with headlights could influence edge detection and area of interest significantly
####9. and many more...

###3. Possible improvements to the pipeline
####1. Using a different color space than gray, e.g. hsl or hsv
####2. Detect cars and take all lines associated with them out of the line detection algorithm
####3. Use different sensors besides camera (LiDar etc.) for verifying results (sensor fusion)
####4. Changing parameters/thresholds based on conditions  (e.g. look for brighter lines in daylight)
####5. Correct camera distortion
####6. and many more...
