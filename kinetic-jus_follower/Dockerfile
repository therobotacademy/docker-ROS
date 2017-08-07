FROM therobotacademy/ros-catkin:kinetic-robot-armhf

MAINTAINER Bernardo Ronquillo

ENV DEBIAN_FRONTEND noninteractive

#RUN apt-get update ; apt-get install -y git

# Make sure bash is the standard shell

RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Create the package jus_follower

RUN /bin/bash -c "source /opt/ros/kinetic/setup.bash && \
                  cd ~/catkin_ws/src && \
                  catkin_create_pkg jus_follower && \
                  cd ~/catkin_ws && \
                  catkin_make && \
                  source ~/catkin_ws/devel/setup.bash"

# Clone the source code for the Robot
RUN /bin/bash -c "source /opt/ros/kinetic/setup.bash && \
                  source ~/catkin_ws/devel/setup.bash && \
	          roscd jus_follower && \
                  git clone https://github.com/therobotacademy/jus_follower && \
                  mv jus_follower src"

VOLUME /dev:/dev

CMD source ~/catkin_ws/devel/setup.bash; roslaunch jus_follower follow_me.launch;
