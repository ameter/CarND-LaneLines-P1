# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 steps. First, I set a number of tunable parameters.  I did this as a separate function because I wanted to set them all in one place.  This simlified tuning as I was able to tweak the parameters and then run my test images or video through my pipeline by only re-executing two cells.  Second, I converted the images to grayscale.  Third, I applied a gaussian blur.  Fourth, I performed Canny edge detection.  Fifth, I applied a mask to the region in front of the camera where I wanted to find lane lines to follow.  Sixth, I applied a Hough transform to identify the lines.  Seventh, I overlaid the identified lane lines on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function to bin all the identified line segments into 2 bins (left and right) based on whether they had a positive or negative slope.  I then extended and averaged the lines in each bin to form a single left and right line.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are no lane lines.  Other techniques would need to be employed ot follow the road.

Another shortcoming could be when there is a lane split, as in certain situations at Interstate exit ramps.  In this case, the car needs to decide which lane to follow.  

Finally, as seen in the challenge video, there are situations where there are multiple lines on the road (that are not lane lines) caused by shadows, changes in pavement types, bridges, etc.  More work is needed to confidently address all of these types of situations that can and will be encountered in a real world situation.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
