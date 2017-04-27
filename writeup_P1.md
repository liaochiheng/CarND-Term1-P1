# **Finding Lane Lines on the Road** 

## Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/lines.png

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps：
1. Graying, and find lines, this code remain the same.
2. Categoty lines by 'check_line' function.
   For each line, i will do the following checks to detect whether it belongs to any category:
   2.1. Calculate the line slope, current category average slope, and all endpoints.
   2.2. If this line cross or close to current category, then check slope only.
   2.3. Else, check all 3 slopes(line slope - current slope, two endpoint pairs slope)
   Make sure all lines with approximate slopes gather together.
3. For each approximate slope, calculate the average slope weighted by length(length*length to be exact) of each line.
4. Filter_lines is to filter out some noise.
5. Deal with dash lines, just extend the y to down-edge.
6. Draw each line by slope, center coordinates, and the endpoints.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

The most tricky functions in my project 'P1.ipynb' should be 'draw-line'.
I defined 2 versions: 'draw_lines2' and 'draw_line3'.
'draw_lines2' only worked with images, not videos.
'draw_lines3' is the final version working fine for all images and videos, except 'extra.mp4'.


### 3. Suggest possible improvements to your pipeline

1. Try other parameters to fix curve-line detection.
