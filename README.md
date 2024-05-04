Introduction
Sensing of 3D information related to the obstacles in front of the vehicle should rely on the stereo vision principle. The ability of an autonomous vehicle to sense obstacles and navigate its surroundings has a key role in the development of modern robots. For this reason we present a project in which a robot, through the principle of stereo vision, is able to perceive the distance of obstacles in front of its view. Such technology could be implemented by a navigation system for autonomous vehicles to automatically avoid obstacles.

Objective
The objective of the project aims to use synchronized video sequences captured by a stereo camera mounted on a moving vehicle to detect spatial information of the frontal environment. The primary task is to develop an area-based stereo matching algorithm capable of generating a dense disparity map from the syncronized stereo camera inputs (robotL.avi for the left view, robotR.avi for the right view). Then by using geometrical calculations an estimated distance from the robot to the central area of the view need to be calculated. Additionally, an alarm is triggered whenever the distance falls below 0.8 meters. Finally, given that in the center of the scene there is a chessboard. The dimension of it (height and width) must be computed. This will be useful in order to compare it to the real values and give an estimation of the accuracy of the method used.

Functional Specifications
In this project we follow a series of steps to achieve the objectives:

Take the dataset
To estimate all the points, it is useful to take the video and the parameters required to estimate distances from stereo images like focal length (f = 567.2 pixel) and baseline (b = 92.226 mm).

Disparity Map Computation
Compute the disparity map in a central area of the image frame to measure distances in the portion of the environment relevant to the vehicle's trajectory.

Main Disparity Estimation
Estimate the main disparity for the frontal portion of the environment based on the disparity map of the central area of the reference frame.

Distance Calculation
Determine the distance of the obstacle from the moving vehicle based on the main disparities estimated from each pair of frames.

Output Generation and Alarm Trigger
Generate output conveying distance information to the user and trigger an alarm when the distance falls below a predefined threshold (0.8 m).

Estimate the size of the board
Use the found board corners to estimate the size of the board. Then compare it with the real size of the known one (125mm x 178mm)

Suggested Improvements
Several improvement can be followed:

Disparity Map Computation with the offset
The matching algorithm could be modified to deploy a smaller disparity range with an offset. This offset can be computed knowing the value of the main disparity, d_main, computed at the previous time instant. Accordingly, as the vehicle gets closer to the obstacle, the horizontal offset increases, thus avoiding the main disparity to exceed the disparity range (and conversely, when the vehicle goes away from the obstacle).

From one disparity to more
Instead of just a single main disparity, a set of disparities can be computed and associated with the different areas of the obstacle, so to then estimate the distance from the camera for each part of the obstacle. For example, the image may be divided into 5 large vertical stripes, assuming the vertical lines to be parallel to the obstacle and the image plane of the stereo sensor, we then estimate a main disparity value for each stripe. A planar view of the obstacle could be created by computing the angle between the horizontal lines parallel to the obstacle and the image plane of the stereo sensor.

Develop a more robust approach to estimate the main disparity
Ambiguous disparity measurements may be detected and removed by analysing the function representing the dissimilarity (similarity) measure along the disparity range or by computing disparities only at sufficiently textured image points. Disiparities could be computed by using the salient image points.
