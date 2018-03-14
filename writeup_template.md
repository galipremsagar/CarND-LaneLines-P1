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

My pipeline consisted of 5 steps. 
First, I converted the images to grayscale. Next, I've applied gaussian blur to the grayscale image. Post that I've detected edges using canny edge detection method of opencv. Next I've built a numpy array which is essentially polygon co-ordinates. Then I've extracted the region of interest using the polygon co-ordinates. With that images I've used hough transform to detect lines and plot them on the actual image. There are certain parameters which I've used as part of this function implementation, as suggested in the lectures I have gone with 1:3 ratio of threshold values of canny edge detection. Which is why I choose 75 & 150 as min & max thresholds so that human eye can also detect the range of colors easily between those thresholds. For the hough transform the parameters mostly I've found after multiple number of iterations. I almost spent 2 days completely on attaining a perfect combination of paramters. From my understanding rho & theta values are pretty generic but the min line gap and max line gap is what took time for me to figure out. I could've gone with 10 for both the min line len & max lines gap...but then I felt 25 to be much better as that gives stronger lines in the image. 


### 2. Identify potential shortcomings with your current pipeline

Most of the issues of lines flickering in the image I could resolve by tinkering around wide range of paramters for edge detection and hough transforms. But there could be one major potential shortcoming with my pipeline. What if there are too many edges in my region of interest? What if there are too many vehicles in my region with quite visible edges :) Then there will be too many edges detected.


### 3. Suggest possible improvements to your pipeline

Hough transforms works perfectly to detect straight lines & that's why all the first videos came out pretty well. But the last optional  challenge video turned out to be challenging to the hough transforms we were applying. Instead of hough..we should also do some additional mathematical processing and apply RANSAC as mentioned in this stack overflow link: https://stackoverflow.com/a/10220873
So the possible improvement is inclusion of the steps mentioned in the algorithm provided in the link
