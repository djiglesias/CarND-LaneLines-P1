# **Finding Lane Lines on the Road** 
---

## 1. Pipeline Overview

The following steps were used detect lane lines in the image:
- Grayscale
- Edge Detection
- Region of Interest
- Hough Lines
- Image Overlay

### Convert to Grayscale
Converting the image from RGB (left) to Grayscale (right) reduces the image size by a third and unifies white and yellow lane lines. With all colour gradients removed, the image is now primed for edge detection using the gradient in grayscale shades.

| ![alt text][image1] | ![alt text][image2] |
|:---:|:---:|

### Edge Detection
The grayscale image (left) is processed for edges (right) by using OpenCV to draw lines along all the regions where there is a distinct threshold in the gradient. The threshold is controlled by adjust the upper and lower limits to filter out unwanted spectrums of the gradient.

| ![alt text][image2] | ![alt text][image3] |
|:---:|:---:|


### Region of Interest
The image returned from the edge detection function (left) contains artifacts from undesired portions of the image (horizon, shoulder, street signs... etc) and these should be removed to increase the quality of the lane detection function. These are removed by applying a mask over the image that eliminates all features outside of a polygon (defined by four vertices) that defines the region most probable to contain lane lines. The result is the same image with (hopefully) only edges from lane lines (right).

| ![alt text][image3] | ![alt text][image4] |
|:---:|:---:|


### Hough Lines
Applying the Hough Lines function to the masked image (left) returns a set of lines defined by two sets of points ((x1,y1),(x2,y2)). This set is passed to the function draw_lines() that categorizes each line as left, right, or noise based on the slope. If the line is a left or a right lane line then its slope and y-intercept are computed using **y = m\*x + b** with each set of points and appended to a list specific to each lane. Once all the lines have been examined, a single left and right lane line is drawn using the mean slope and y-intercept (right).


| ![alt text][image4] | ![alt text][image5] |
|:---:|:---:|


### Lane Line Overlay
Using the magnitude() function, the lane lines image returned from the previous step is superimposed onto the original image using a semi-transparent mask to give the final image (below).

![Alt Text][gif]


## 2. Shortcomings of Current Pipeline
As with all software, there are always short comings and drawbacks to the methodology used. For this project the major drawbacks were due to assumptions made in order for this to remain a beginner level project. The function to detect and overlay lane lines onto an image (or stream of images) was limited to a linear based model. If the lane lines were to bend, as would be observed on a corner, then the function would neglect the polynomial behaviour of such a line and consider only the slope between the start and end of the line segment. This generalization limits the algorithm to straight stretches of road.


## 3. Possible Pipeline Improvements
The computing efficiency of this algorithm could be dramatically increased in a number of possible ways since there is quite a bit on unnecessary computation performed on this image. Such improvements would be to reduce the image quality as to limit the number of pixels to be processed on each image, and to create a new subimage from the region of interest imediately after applying the greyscale.


[//]: # (Image References)

[gif]:    ./examples/solidYellowLeft.gif "Lane Lines"
[image1]: ./examples/original.jpg  "Original"
[image2]: ./examples/grayscale.jpg "Grayscale"
[image3]: ./examples/canny.jpg     "Canny"
[image4]: ./examples/roi.jpg       "Region of Interest"
[image5]: ./examples/houghline.jpg "Houghs Lines"
[image6]: ./examples/weighted.jpg  "Weighted Image"
