# Advance-Lane-Line-Detection
This gives a more robust output than the SimpleLaneLine Finder
Advance Lane Detection

This basically consist of few steps(respectively)

1.	Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
2.	Apply a distortion correction to raw images.
3.	Use color transforms, gradients, etc., to create a thresholder binary image.
4.	Apply a perspective transform to rectify binary image ("birds-eye view").
5.	Detect lane pixels and fit to find the lane boundary.
6.	Determine the curvature of the lane and vehicle position with respect to center.
7.	Warp the detected lane boundaries back onto the original image.
8.	Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

# All these steps are well defined with the code in ‘description.Ipynb’

•	First, we have to correct camera distortions, which are most likely to occur in corners, otherwise the distorted image gives false inputs.

•	For a specific camera this was done by using the help of chessboards images due to its robust corners and sharp intensity/contrast We use various angles and distances of a specific chessboard to calculate 2 arrays. One is objpoints and other is imagepoint. These arrays act as a trained model for that specific camera so in case of a distorted input by using these 2 array values, function outputs the undistorted image.

•	Then we need to extract the lane lines. From past results it has shown that among RGB, HLS or HSV color spaces, best output gives by the s-channel of the HLS color space.

•	Not only that we could use the thresholding such as with the help of sobel kernel. Magnitude and directional thresholding are also useful. In sobel thresholding, we use ‘x’ orientation (kernel) because of we need to find the vertical lines. Because the x-orientation of sobel vector is  the differentiation with respect to x axis of an image by each row.

•	For better result we have seen that combination of these 3 thresholding is good and by summing up the binary image of HLS-transformation (s-channel thresholding), we can enhance the output even more.

•	Then we apply the warp function that is basically give the ‘Bird Eye’ view of our plane street. This was done by calculate a matrix using 4 specific points (more accurately the region that represent the lane lines).

•	After this perspective transformation we detect lane pixels and fit to find the lane boundary.

•	Then we determine the curvature of the lane and vehicle position with respect to center.

•	After detecting the perfect polynomial curves for both left and right lanes, using the inverse matrix of the perspective transformation, we paste these 2 polynomials back to the original image.

•	In additional, we calculate the radius and the distance of vehicle relevant to the center of the road.


## Problems

The ‘project_output_video’ and ‘challenge’ videos have given reasonable outputs but the ‘harder challenge’ one gives very false output.

In this harder challenge, due to higher bending of lane lines, the region of interest is not the same and it changes throughout the video.


## Implementations

•	We could do a gamma correction to the frames that their intensity levels are lower than other frames for increase the accuracy

•	We need to either increase the number of frames for selection a low overhead of an image road lines in order to reduce the errors in road bends.


![Undistorted(Calibration img)](/READ_ME/snap2.png)       Undistorted(Calibration img)

![Undistorted(CVideo snapshot)](/READ_ME/snap3.png)       Undistorted(CVideo snapshot)

![Thresholded Gradient](/READ_ME/snap4.png)               Thresholded Gradient

![Thresholded Magnitude](/READ_ME/snap5.png)               Thresholded Magnitude

![Thresholded Grad. Dir.](/READ_ME/snap6.png)              Thresholded Grad. Dir.

![Combined](/READ_ME/snap7.png)                            Combined

![Pipeline Result](/READ_ME/snap8.png)                     Pipeline Result

![Warp Region](/READ_ME/snap9.png)                         Warp Region

![Undistorted & Warped Image](/READ_ME/snap10.png)          Undistorted & Warped Image

![Binary Warped Image](/READ_ME/snap11.png)                 Binary Warped Image

![Lane Line Pixels](/READ_ME/snap12.png)                    Lane Line Pixels

![Round the polynomials](/READ_ME/snap1.png)               Round the polynomials

![Combine the result with the original image](/READ_ME/snap13.png)  Combine the result with the original image








