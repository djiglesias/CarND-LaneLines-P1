# **Finding Lane Lines on the Road** 
---

## 1. Pipeline Overview

The following steps were used detect lane lines in the image:
- Convert to grayscale.
- Use Canny for edge detection.
- Apply region of interest.
- Apply Hough Lines.
- Overlay lines on original image.

### Convert to Grayscale
Converting the image from RGB (left) to Grayscale (right) reduces the image size by a third and unifies white and yellow lane lines. With all colour gradients removed, the image is now primed from edge detection using the gradient in grayscale shades.

| ![alt text][image1] | ![alt text][image2] |
|:---:|:---:|

### Edge Detection
The grayscale image (left) is processed for edges (right) by using OpenCV to draw lines along all the regions where there is a distinct threshold in gradient. The threshold is controlled by adjust the upper and lower limits to filter out unwanted spectrums of the gradiate.

| ![alt text][image2] | ![alt text][image3] |
|:---:|:---:|


### Region of Interest
The image returned from the edge detection function (left) contains artifacts from undesired portions of the image (horizon, shoulder, street signs... etc) and there should be removed to increase the quality of the lane detection function. These are removed by applying a mask over the image that eliminates all features outside of a polygon (defined by four vertices) that defines the region most probable of containing lane lines. The result is the same image with (hopefully) only edges from lane lines (right).

| ![alt text][image3] | ![alt text][image4] |
|:---:|:---:|


### Hough Lines
Applying the Hough Lines function to the masked image (left) returns a set of lines defined by two sets of points ((x1,y1),(x2,y2)). This set is passed to the function draw_lines() that categorizes each line as left, right, or noise based on the slope. 

y = m*x + b 

| ![alt text][image4] | ![alt text][image5] |
|:---:|:---:|


### Draw Lines
| ![alt text][image5] | ![alt text][image6] |
|:---:|:---:|



## 2. Shortcomings of Current Pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...




## 3.Possible Pipeline Improvements

A possible improvement would be to ...

Another potential improvement could be to ...




[//]: # (Image References)

[image1]: ./examples/original.jpg  "Original"
[image2]: ./examples/grayscale.jpg "Grayscale"
[image3]: ./examples/canny.jpg     "Canny"
[image4]: ./examples/roi.jpg       "Region of Interest"
[image5]: ./examples/houghline.jpg "Houghs Lines"
[image6]: ./examples/weighted.jpg  "Weighted Image"
