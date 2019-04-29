## Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


The goals / steps of this project are the following and these are explained with examples in the writeup.md file

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

# Issues and challenges
1. For getting the perpective transform the challenge was to how to get the proper source and destination so that view is in particular paralle lanes.
2. Another challenge was of the sliding window search to make sure the pixels which are visible are detected easily and used.
3. And then of the colour thresholds to determine such that the yellow and the white part detected well 








