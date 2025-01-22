# Pull ROS2 Foxy Container
FROM osrf/ros:humble-desktop

SHELL ["/bin/bash","-c"]

# Install Python
RUN apt update && apt install -y python3-pip

RUN sudo apt install python3-colcon-common-extensions

# Set Up Workspace
RUN mkdir -p ./carla-ros-bridge
WORKDIR /root/carla-ros-bridge

RUN git clone --recurse-submodules https://github.com/ttgamage/carla-ros-bridge.git src/ros-bridge

RUN rosdep update && rosdep install --from-paths src --ignore-src -r

RUN sudo apt install ros-humble-derived-object-msgs

RUN source /opt/ros/humble/setup.bash && colcon build

COPY ros_entrypoint.sh /

RUN ["sudo", "chmod", "+x", "/ros_entrypoint.sh"]

ENTRYPOINT ["/ros_entrypoint.sh"]

RUN python3 -m pip install --upgrade pip && python3 -m pip install numpy pygame

RUN python3 -m pip install 'carla==0.9.15'


##Below may be necessary for ros bridge python compatibility
# Set the working directory
#WORKDIR /python-files

# Copy the CARLA Python API wheel and egg files into the container
#COPY carla-0.9.15-cp310-cp310-linux_x86_64.whl /python-files/
#COPY carla-0.9.15-py3.10-linux-x86_64.egg /python-files/

# Install the CARLA Python API wheel
#RUN python3 -m pip install /python-files/carla-0.9.15-cp310-cp310-linux_x86_64.whl

# Set the PYTHONPATH to include the ROS bridge egg
#ENV PYTHONPATH="/python-files/carla-0.9.15-py3.10-linux_x86_64.egg:$PYTHONPATH"