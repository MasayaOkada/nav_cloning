FROM tiryoh/ros-desktop-vnc:melodic

ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && \
	apt upgrade -y && \
RUN curl -kL https://bootstrap.pypa.io/get-pip.py | python
ENV PATH $PATH:/home/${DOCKER_USER}/.local/bin
RUN pip install chainer==6.0 && \
    pip install scikit-image
# workspace 
RUN mkdir -p ~/catkin_ws/src &&\
    cd ~/catkin_ws/src && \
    catkin_init_workspace && \
    cd ../ && \
    catkin_make
# setup nav_cloning
RUN cd ~/catkin_ws/src && \
	wget https://raw.githubusercontent.com/MasayaOkada/nav_cloning/master/nav_cloning.install && \
    wstool init && \
    wstool merge nav_cloning.install && \
    wstool up && \
    rosdep install --from-paths . --ignore-src --rosdistro $ROS_DISTRO -y && \
    catkin_make && \
	apt autoremove -y && \
	apt clean && \
	rm -rf /var/lib/apt/lists/*