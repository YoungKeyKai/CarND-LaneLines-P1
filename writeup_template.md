# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline basically follows the given steps from the introduction tutorial.
1. Takes the raw image and transform it to HSV to prepare for colour thresholding.
1. Colour threshold based on hue and saturation found using histograms.
1. Convert the resulting image to greyscale and smooth it to prepare for canny edge detection.
1. Perform Canny edge detection with parameters that are found based on trial-and-error.
1. Filter off non-lane marking regions by providing the four vertices of a trapezoid. Again, the vertices are determined based on visual approximation from output images. The four vertices' x-values are labeled X1, X2, X3, and X4 from left to right.
1. Run Hough line detection on the filtered image. Here, the default helper had to be modified to also return the list of lines so they can be converted to points for RANSAC.
1. Separate the points from the previous step into right and left lane markings.
1. Run RANSAC on the list of points by picking at a minimum 2 points at a time to train up until a maximum of 500 training cycles.
1. The final lane markings are drawn between points whose x-values corresponded to the region of interest trapezoid's x-values. The corresponding y-values are the RANSAC model's prediction for each x-value.

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...

![alt text][image1]

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
