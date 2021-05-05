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

My pipeline consisted of 2 parts with substeps. 
To explain the steps I am taking below example image.

![alt text][./test_images/solidYellowCurve2masked.jpg]

**Part1.** _Create a Masked image with detected edges and Region of Interest:_**
   1. Converted Image to gray scale and apply Gaussian filter with KERNEL size = 3
      ![alt text][./images_for_writeup/solidYellowCurve2Gaussian.jpg]

   2. Identified edges using Canny edge detector 
      ![alt text][./images_for_writeup/solidYellowCurve2Canny.jpg]
   
   3. Narrowed the detection area using Region of Interest
      ![alt text][./images_for_writeup/solidYellowCurve2ROI.jpg]


**Part2.** _Highlight the detected lanes on the original image:_**
           This is done using hough Transform and which results in a set of lines for both left and right lane.
            To get only one line I took average of the left and right lines and used it to Draw on the image
   1. Applied hough transform to the masked image resulted from step-3
      ![alt text][./images_for_writeup/solidYellowCurve2ROI.jpg]
   
   2. Take average of the lines and Draw those lines on the original image. This is done by merging the two images and applying weights. Below image is the finale result
      ![alt text][./images_for_writeup/solidYellowCurve2ROI.jpg]

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

This is very basic Lane detection algorithm confined to work on limited images. It may not work well especially on
curved or steep curved images. The Algorithm also lacks exact identification of the left and right lanes starting point.
I took the bottom end points as starting points. This may not work well in all cases and may end up detecting shoulder lines.
Also this algorith faces limitation of illumination for eg. it may not work well on different shades of day and night.


### 3. Suggest possible improvements to your pipeline

A more matured and mathematical algorithm is needed where we take into account HSV for better color detection (different color lanes) histograms for identifying starting points for the left and right lanes and many other stable and advanced techniques.
