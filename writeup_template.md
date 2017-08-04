# **Finding Lane Lines on the Road Writeup** 


The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I conducted a gaussian blur, used canny edge detection, region masking and finally a hough transform.

# Grayscaling 

Grayscaling the image leaves an 8-bit image 

# Gaussian Blur

Gaussian smoothing supresses noise and spurious gradients. I selected a Kernel size of 5 for this gaussian smoothing. 

# Canny edge detection

Here is used the canny algorithm to find individual pixels that have the strongest gradient.


# Hough transform 


In image space, we plot lines as y = mx + b. In Hough space, we plot lines as m vs b, instead of x vs y.

The hough transform is a transformation from the image space to the hough space. 

A line in image space represents a point in hough space and point in image space corresponds with a line in hough space. 

Two points in image space correspond with two lines in hough space and these lines must intersect. This point of intersection represents the line y = mx + b.

Therefore to find lines in image space, we will look for intersecting lines in hough space. 

We devide our hough space into a gird and then define intersecting lines as all the lines passing through this grid.

Because vertical lines have infinite slope in m b representation, we need a new parameratisation. 

We redefine the line in polar coordinates and use rho and theta, where:

- Rho is the distance of the line from the origin and is in units of pixels

- Theta is the angle away from the horizontal and is in radians. 

Now each point in image space corresponds to a sine curve in hough space and the intersection of the sine curves in rho theta space gives the parametisation of the line. 

We specifcy the threshold paramater which specifies the number of intersections in a grid cell must have for it to be significant. Rho takes a minimum value of 1 and theta starts at pi/180 in radians.

The min line len is the minimum legnth of the line that we will accept in the output and the max line gap is the maximum distance between segments that we will allow to be connected to a single line. 


# Line extrapolation 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
