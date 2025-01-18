# Pull ROS2 Foxy Container
FROM osrf/ros:foxy-desktop-focal

SHELL ["/bin/bash","-c"]

# Install Python
RUN apt update && apt install -y python3-pip

RUN sudo apt install python3-colcon-common-extensions

# Set Up Workspace
RUN mkdir -p ~/carla-ros-bridge
WORKDIR /root/carla-ros-bridge

RUN git clone --recurse-submodules https://github.com/carla-simulator/ros-bridge.git src/ros-bridge

RUN rosdep update && rosdep install --from-paths src --ignore-src -r

RUN sudo apt install ros-foxy-derived-object-msgs

RUN source /opt/ros/foxy/setup.bash && colcon build

COPY ros_entrypoint.sh /

RUN ["sudo", "chmod", "+x", "/ros_entrypoint.sh"]

ENTRYPOINT ["/ros_entrypoint.sh"]

RUN python3 -m pip install --upgrade pip && python3 -m pip install numpy pygame

RUN python3 -m pip install 'carla==0.9.13'