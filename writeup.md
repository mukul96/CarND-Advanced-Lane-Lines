
## Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


In this project, the goal was to write a software pipeline to identify the lane boundaries in a video.There were many challenges from caliberation, transfroming,color spacing and more


These are the following steps of the project that were followed and the attatched are the images so that to show how my code is written and the flow was made.

### Camera Calibration

#### 1. Briefly state how you computed the camera matrix and distortion coefficients. Provide an example of a distortion corrected calibration image.

The code for this step is contained in the first code cell of the jupyter notebook 

I start by preparing "object points", which will be the (x, y, z) coordinates of the chessboard corners in the world. Here I am assuming the chessboard is fixed on the (x, y) plane at z=0, such that the object points are the same for each calibration image.  Thus, `objp` is just a replicated array of coordinates, and `objpoints` will be appended with a copy of it every time I successfully detect all chessboard corners in a test image.  `imgpoints` will be appended with the (x, y) pixel position of each of the corners in the image plane with each successful chessboard detection.  

I then used the output `objpoints` and `imgpoints` to compute the camera calibration and distortion coefficients using the `cv2.calibrateCamera()` function.  I applied this distortion correction to the test image using the `cv2.undistort()` function and obtained this result: 

![undistorted image conversion](/output_images/undistort.png)

#### 2. Describe how (and identify where in your code) you used color transforms, gradients or other methods to create a thresholded binary image.  Provide an example of a binary image result.
I used a combination of color and gradient thresholds to generate a binary image like the red and green thresholds required for produciing the yellow color and also the S and L channel thresholds as from the hsl image you can view that the s and L channels produce better intensity of the yellow and white lanes. 
![hsl image](/output_images/hsl.png)
and then the binary image was produced by applying proper thresholds like this
![thresholded image](/output_images/thresholded.png)

#### 3. Describe how (and identify where in your code) you performed a perspective transform and provide an example of a transformed image.

The code for my perspective transform includes a function called cv2.warpPerspective, which appears in the block of perspective transform

```python
src = np.float32(
    [[(img_size[0] / 2) - 55, img_size[1] / 2 + 100],
    [((img_size[0] / 6) - 10), img_size[1]],
    [(img_size[0] * 5 / 6) + 60, img_size[1]],
    [(img_size[0] / 2 + 55), img_size[1] / 2 + 100]])
dst = np.float32(
    [[(img_size[0] / 4), 0],
    [(img_size[0] / 4), img_size[1]],
    [(img_size[0] * 3 / 4), img_size[1]],
    [(img_size[0] * 3 / 4), 0]])
```

This resulted in the following source and destination points:

| Source        | Destination   | 
|:-------------:|:-------------:| 
| 220,720      | 320,720        | 
| 1110,720     | 920,720        |
| 570,470      | 320, 1         |
| 722,470      | 920, 0         |

![warped image](/output_images/warped.png)

#### 4. Describe how (and identify where in your code) you identified lane-line pixels and fit their positions with a polynomial?

Then I did sliding window search with some margin of 100 and window frames of 10 and got this result and fit my lane lines with a 2nd order polynomial kinda like this.
![lane lines](/output_images/lanelines.png)
it's code is in the sliding window search block

#### 5. Describe how (and identify where in your code) you calculated the radius of curvature of the lane and the position of the vehicle with respect to center and combined the warped image into original image.
Then determined the curvature of the lane and vehicle position with respect to center(code in raduis of curvature block) and warped the image back into the original image.The text was added to the image in the last step of pipeline.
![completeImageWithArea](/output_images/completeImageWithArea.png)

6. The above image consists of everything from the bird view perspective and lanes area covered with the radius of curvature



### Pipeline (video)
The output of the `project_video.mp4` is present in the repository of the name
`project_video_output.mp4` and the complete pipeline is worked on it.



# Issues and challenges
1. For getting the perpective transform the challenge was to how to get the proper source and destination so that view is in particular paralle lanes.
2. Another challenge was of the sliding window search to make sure the pixels which are visible are detected easily and used.
3. And then of the colour thresholds to determine such that the yellow and the white part detected well 
