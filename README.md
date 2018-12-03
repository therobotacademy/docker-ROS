# December 2018
Dockerfile placed in root directory to deploy ROS Kinetic in Balena OS



# August 2017
## docker-ROS
Docker images for using  ROS in Robots based in Raspberry Pi SBC

These images are built on top of esteve/ros:kinetic-robot-armhf

   * **Dockerfile** in folder *kinetic-robot-armhf* -> ROS Kinetic for ARMHF devices

      - BUILD THE IMAGE:
```
$ docker build -t local/ros-catkin:kinetic-robot-armhf .
```
      - RUN A BASH SESSION:
```
$ docker run --name ros-kinetic -it local/ros-catkin:kinetic-robot-armhf
```

   * **Dockerfile** in folder *kinetic-jus_avoid* -> Robot JUS, package 'jus_avoid'. Try by running in the shell the command 'roslaunch jus_avoid avoid_obstacles.launch'


      - BUILD THE IMAGE:
```
$ docker build -t local/ros-catkin:kinetic-jus_avoid .
```
      - RUN A BASH SESSION:
```
$ docker run --name ros-jus_avoid -it --privileged local/ros-catkin:kinetic-jus_avoid
```
This container includes 'VOLUME /dev:/dev'. So you just need to use the flag '--privileged' for accessing serial devices when running it.

Docker hub URL for pulling the images is:

https://hub.docker.com/r/therobotacademy/ros-catkin/
