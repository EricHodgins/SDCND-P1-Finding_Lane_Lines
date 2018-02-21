# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps. 
1. First I converted the image to grayscale.
2. Then I used a Gaussian Blur to blur the image.  Hopefully removing noise and sporadic gradients.
3. Then I used the Canny Edge Detector Algorithm to detect lines.
4. Then I mask out a region of the picture leaving only the pixels that contain the lines needed.
5. Then I apply a Hough Transform to find the line data.
6. Taking the line data from the Hough Transform I separate the data into left and right lines.
7. Then I use a polyfit (linear best fit) on the line data to find slope and y-intercept. Using this I choose a y max
   value (or height limit) on the line.  Extrapolating these two points I now have the line needed.
8. I then draw the line onto the the image using the draw_lines method.



### 2. Identify potential shortcomings with your current pipeline

A few shortcomings is that I fit the line data to a linear model.  When the road is curvy my method probably won't
work well.  I've hardcoded the masked region assuming the camera will be centered.  This may not be true.  I always
assume there will be line data to collect.  Steep hills may also be a problem.


### 3. Suggest possible improvements to your pipeline

Fit the line model to a non-linear model.  Don't hardcode the masked region.
