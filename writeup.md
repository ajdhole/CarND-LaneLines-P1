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

# Reflection

## My reflection consist of below steps:

Current pipeline
Based on number of iterations, my current pipeline is as follows:

1) To identify lane line from image based on their color, I have converted image from RGB to HLS with function convert_hls().
    
2) After converting image to hls, select_white_yellow(img) used to filter yellow and white color based based on their range, This command filter out white and yellow color line from image even if lane line passing through tree shades.

3) Then image converted to grayscale with grayscale() function.

4) After grayscale canny edge detected with cv2.canny function with low threshold 50 and high threshold 150.

5) cv2.GaussianBlur applied to smoothing edges.

6) To mask required area on image, Create a trapezoidal region-of-interest in the center lower-half of the image: region_of_interest(), also vertices defined for region of interest such that it will be suitable for any size of image.

7) Apply Hough Line Transform to detect line in image, optimize following Hough Line parameter for 
	best result:

	rho – Distance resolution of the accumulator in pixels.
	theta – Angle resolution of the accumulator in radians.
	threshold – Accumulator threshold parameter. Only those lines are returned that get enough votes (> threshold).
	minLineLength – Minimum line length. Line segments shorter than that are rejected.
	maxLineGap – Maximum allowed gap between points on the same line to link them.

8) Since Hough Line Transform Detected number of lines, we have to average this line in single line which representing Lane line. For this draw_Line function modified. First all Left Lane Line and Right Lane  Line separated with their respective slope value. With the help of Polyfit function get their slope and intercept, with this and Y point on image we can calculate X point, and line with cv2.line functions.

9) Line image overlap on original image with cv2.addWeighted function.

10) Finally video processed with VideoFileClip module from moviepy.editor library. 


### 2. Identify potential shortcomings with your current pipeline

1) Algorithm poorly performing on lane with curvature, also it is color sensitive.

2) we need to check out for different road profiles with different curvature data.

3) This program is applicable on empty road where there is no traffic, we have not yet validate traffic  conditions, also different weather conditions like raining, Lane detection at night.


### 3. Suggest possible improvements to your pipeline

1) we need to simulate different road conditions like lane data, different weather conditions, checking at road traffic.This can be achieved by implementing robust computer vision and deep learning technology.