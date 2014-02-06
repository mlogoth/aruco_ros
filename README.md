aruco_ros
=========

Software package and ROS wrappers of the Aruco Augmented Reality marker detector library

### Features
<img align="right" src="https://raw.github.com/pal-robotics/aruco_ros/master/etc/marker_in_hand.jpg" />
 * High-framerate tracking of AR markers
 * Generate AR markers with given size and optimized for minimal perceptive ambiguity (when there are more markers to track)
 * Enhanced precision tracking by using boards of markers
 * ROS wrappers
 

### Applications

 * Object pose estimation
 * Visual servoing: track object and hand at the same time

<img align="right" src="https://raw.github.com/pal-robotics/aruco_ros/master/etc/reem_gazebo_floating_marker_world.png"/>
### Test it with REEM

 * Open a REEM in simulation with a marker floating in front of the robot. This will start the stereo cameras of the robot too. Since this is only a vision test, there is nothing else in this world apart from the robot and a marker floating in front of it. An extra light source had to be added to compensate for the default darkness.

    ```
    roslaunch reem_gazebo reem_gazebo.launch world:=floating_marker
    ```
 * Launch the `image_proc` node to get undistorted images from the cameras of the robot.
 
    ```
    ROS_NAMESPACE=/stereo/right rosrun image_proc image_proc image_raw:=image
    ```
 * Start the `single` node which will start tracking the specified marker.
 
    ```
    roslaunch aruco_ros single.launch markerId:=26 markerSize:=0.08 eye:="right" side:="r"
    ```
 * Visualize the result
 
    ```    
    roslaunch reem_gazebo reem_gazebo.launch world:=floating_marker
    ```


<img align="right" src="https://raw.github.com/pal-robotics/aruco_ros/master/etc/reem_gazebo_floating_marker.png"/>
