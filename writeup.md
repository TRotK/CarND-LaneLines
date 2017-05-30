# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[fig1]: ./test_images_output/line_segments/solidWhiteCurve.jpg
[fig2]: ./test_images_output/line_segments/solidWhiteRight.jpg
[fig3]: ./test_images_output/line_segments/solidYellowCurve.jpg
[fig4]: ./test_images_output/line_segments/solidYellowCurve2.jpg
[fig5]: ./test_images_output/line_segments/solidYellowLeft.jpg
[fig6]: ./test_images_output/line_segments/whiteCarLaneSwitch.jpg

[fig7]: ./test_images_output/lane_marks/solidWhiteCurve.jpg
[fig8]: ./test_images_output/lane_marks/solidWhiteRight.jpg
[fig9]: ./test_images_output/lane_marks/solidYellowCurve.jpg
[fig10]: ./test_images_output/lane_marks/solidYellowCurve2.jpg
[fig11]: ./test_images_output/lane_marks/solidYellowLeft.jpg
[fig12]: ./test_images_output/lane_marks/whiteCarLaneSwitch.jpg

[vid1]: ./test_videos_output/solidWhiteRight.mp4

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

#### My pipeline is as follows. 

* I converted the images to grayscale.
* I applied Gaussian smoothing with kernel size of 5 to suppress noise.
* I applied Canny edge detection on the smoothed image with low threshold being 80 and high threshold 180.
* I specified the region of interest as a trapezoid and used it to filter out all the edges outside of the region. Since the camera is not exactly centered, my mask was shifted as well.
* I ran Hough transform with rho = 2, theta = pi / 180, threshold = 20, min_line_length = 10 and max_line_gap = 10.

![alt text][fig1]
![alt text][fig2]
![alt text][fig3]
![alt text][fig4]
![alt text][fig5]
![alt text][fig6]

#### In order to draw a single line on the left and right lanes, I modified the draw_lines() as my_draw_lines().

* I separated the hough line segments into two groups according to their slope and position (left/right) on the image.
* I applied linear regression on two sets of line segments, respectively, to estimate two line equations.
* According to the estimated line parameters, I drew only one line on the left and right lanes at their reasonable position.

![alt text][fig7]
![alt text][fig8]
![alt text][fig9]
![alt text][fig10]
![alt text][fig11]
![alt text][fig12]

#### Test on Videos:

* The pipeline works well on solidWhiteRight.mp4 and solidYellowLeft.mp4. The resulting videos are in the folder test_videos_output.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...


### 4. Optional challenge

In order to 