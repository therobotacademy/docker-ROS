# This Dockerfile adds a catkin workspace to the
# kinetic-ros-robot image. The workspace is initialized
# at /catkin_ws.
#FROM ros:indigo-ros-base # ROS version for which this Dockerfile was originally prepared
FROM esteve/ros:kinetic-robot-armhf

MAINTAINER Bernardo Ronquillo

# Needed to suppress warning when installing g++:
# debconf: unable to initialize frontend: Dialog
# debconf: (TERM is not set, so the dialog frontend is not usable.)
# debconf: falling back to frontend: Readline
# ...
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update ;  apt-get install -y nano

# add environment setup 
RUN /bin/bash -c "echo 'source /opt/ros/kinetic/setup.bash' >> ~/.bashrc"

# Setup catkin workspace
RUN /bin/bash -c "source /opt/ros/kinetic/setup.bash && \
                  mkdir -p ~/catkin_ws/src && \
                  cd ~/catkin_ws/src && \
                  catkin_init_workspace && \
                  cd ~/catkin_ws/ && \
                  catkin_make && \
                  echo 'source /catkin_ws/devel/setup.bash' >> /.bashrc"

RUN bin/bash -c "source ~/.bashrc"
