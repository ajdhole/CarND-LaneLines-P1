# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./CarND-LaneLines-P1/laneLines_thirdPass.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My reflection consist of below steps:

***Current pipeline***
###Based on number of iterations, my current pipeline is as follows:
###convert color image into hls with convert_hls() to filter out white and yellow channel
*Keep only yellow and white pixels, black out all other pixels: select_white_yellow()
T*his removes any unwanted edges from shadows, cracks in the road, etc.
*Convert image into grayscale: grayscale()
*Apply Gaussian smoothing: gaussian_blur()
*Run Canny Edge Detector: canny()
*Create a trapezoidal region-of-interest in the center lower-half of the image: region_of_interest()
*Run Hough Line Detector: hough_lines()
*Filter Hough lines by slope and endpoint location, and separate them into candidate right/left lane line segments. 
*Then run linear regression on candidate right/left lane line segment endpoints, to create right/left lane line equations. 
*From these equations, draw right/left lane lines on the image: draw_lines()



### 2. Identify potential shortcomings with your current pipeline


*Algorithm poorly performing on curvature also it is color sensitive, 
*we need to check out for different road profiles with differnt curvature and 
*also if any vehicle in front, need to identify objects for various scenario.


### 3. Suggest possible improvements to your pipeline

*we need to simulate different road conditions like lane data, different weather conditios, checking at road traffic.
