
## Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


In this project, the goal was to write a software pipeline to identify the lane boundaries in a video.There were many challenges from caliberation, transfroming,color spacing and more


These are the following steps of the project that were followed and the attatched are the images so that to show how my code is written and the flow was made.

1. Computing the camera calibration matrix and distortion coefficients given a set of chessboard images and applying the distortion correction to raw images like the below.
![undistorted image conversion](/output_images/undistort.png)

2. Now using color transforms, gradients, etc., to create a thresholded binary image.
![thresholded image](/output_images/thresholded.png)
3. Applying a perspective transform to rectify binary image ("birds-eye view").
![warped image](/output_images/warped.png)
4. Detected lane pixels and fit them to find the lane boundary.
![lane lines](/output_images/lanelines.png)
5. Then determined the curvature of the lane and vehicle position with respect to center and warped the image back into the original image.
![completeImageWithArea](/output_images/completeImageWithArea.png)

6. The above image consists of everything from the bird view perspective and lanes area covered with the radius of curvature



The `challenge_video.mp4` video is the complete architecture represented in the image




