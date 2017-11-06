# **Finding Lane Lines on the Road** 
---

## 1. Pipeline Overview

- describe the pipeline
-- convert to gray scale
-- run canny on image
-- apply region of interest
-- draw hough lines
-- overlay the lines onto the original image with transparency
- describe draw_lines()
-- determine slope and y-intercept for each set of points
-- select all lines with slope between 0.4 & inf
-- draw line with average values from left and right
- describe process_image()
-- run process image, and catch instances where no lines are found



![alt text][image1 =250x]
![alt text][image2 =250x]
![alt text][image3 =250x]
![alt text][image4 =250x]
![alt text][image5 =250x]


## 2. Shortcomings of Current Pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...




## 3.Possible Pipeline Improvements

A possible improvement would be to ...

Another potential improvement could be to ...




[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./examples/canny.jpg     "Canny"
[image3]: ./examples/roi.jpg       "Region of Interest"
[image4]: ./examples/houghline.jpg "Houghs Lines"
[image5]: ./examples/weighted.jpg  "Weighted Image"
