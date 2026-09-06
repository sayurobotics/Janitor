# About this Janitor project:
This project is to create a robot for hotel washroom cleaning purpose.
This is a mobile 4 wheeled robot with vertical lift, 1-dof rotating arm for water spray, air dry and vacuum cleaning. Camera and lidar in the robot for navigation and vision. It will use VLA for cleaning sink, toilet, etc. and navigation (within bathroom) for cleaning floor.

# To install realsense camera drivers in host:
 - [realsenseai.com/developers/get-started](https://www.realsenseai.com/get-started/)
 - https://github.com/realsenseai/librealsense/blob/development/doc/distribution_linux.md

# Setup isaac-ros:

## Note:
Download this repo and rename the root folder of this repo from "Janitor" to "isaac_ros-dev", which should be located in ~/workspaces/isaac_ros-dev.

```
ankit@dev-PC-robotics:~/workspaces/isaac_ros-dev$ ls -la
drwxrwxr-x 12 ankit ankit 4096 Sep  7 00:10 .
drwxrwxr-x  3 ankit ankit 4096 Aug 30 14:18 ..
-rw-rw-r--  1 ankit ankit    0 Sep  7 00:33 dependencies.repos
drwxrwxr-x  3 ankit ankit 4096 Sep  4 15:35 docker
drwxrwxr-x  7 ankit ankit 4096 Sep  7 00:11 .git
-rw-rw-r--  1 ankit ankit  258 Sep  7 00:09 .gitignore
drwxrwxr-x  3 ankit ankit 4096 Sep  1 00:37 isaac_ros_assets		(extra folder. not checked in this repo. gitignored it)
drwxrwxr-x  2 ankit ankit 4096 Sep  6 23:47 .isaac-ros-cli
-rw-rw-r--  1 ankit ankit 1981 Sep  7 00:22 README.md
drwxrwxr-x  2 ankit ankit 4096 Sep  4 15:37 scripts
drwxrwxr-x  2 ankit ankit 4096 Aug 30 14:18 src
drwxrwxr-x  2 ankit ankit 4096 Sep  7 00:10 .vscode
```

Also use the below env var for a seamless experience with Nvidia's isaac ros (as per its default path recommendations).

```
ankit@dev-PC-robotics:~/workspaces/isaac_ros-dev$ echo $ISAAC_ROS_WS
/home/ankit/workspaces/isaac_ros-dev/
```

## Links to follow for setup isaac-ros:
 - https://nvidia-isaac-ros.github.io/					(latest -> release 4.6)
 - https://nvidia-isaac-ros.github.io/getting_started/index.html
 - https://nvidia-isaac-ros.github.io/getting_started/sensors/realsense_setup.html
 - https://nvidia-isaac-ros.github.io/concepts/dev_env/index.html
 - [good third party tutorial](https://www.youtube.com/watch?v=V_JVNkAoDzI&list=PLunhqkrRNRhb3Fh0Lby60s4pb-klYLjEP&index=2)
 - https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_apriltag/isaac_ros_apriltag/index.html#quickstart
 - https://nvidia-isaac-ros.github.io/concepts/fiducials/apriltag/tutorial_isaac_sim.html

# Commands:

## isaac-ros commands:
 - isaac-ros activate --build-local
 - isaac-ros activate

## inside container:
 - ros2 launch isaac_ros_examples isaac_ros_examples.launch.py launch_fragments:=realsense_mono_rect,apriltag

## in another terminal (inside container):
 - source /opt/ros/jazzy/setup.bash
 - ros2 topic list
 - rviz2 --ros-args -r /camera_info:=/camera_info_rect

## extra:
 - rs-enumerate-devices
 - realsense-viewer
 - ros2 topic echo /tag_detections
