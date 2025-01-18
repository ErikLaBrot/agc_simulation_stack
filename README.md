
# UWF Autonomous Golf Cart - Simulation Stack
This repository contains the files and information necessary to bring up the simulation stack for the AGC project. This simulation stack uses Docker containers for easy setup and portability. Currently, this stack only works in a linux environment, with Windows portability being a planned feature.



## Requirements
- Ubuntu (24.04 preferred)
- Docker
- Docker Compose
- NVIDIA Container Tools
## Installation
To install, verify that you have the prerequisites installed and they work. Then, clone this repository and navigate to it. 

Installation from here is as simple as running docker compose like so:

```
docker compose build 
```
## Running Simulation
Currently, the carla-ros-bridge example is hard coded to start. This example can be started by doing the following:

Open a terminal window, and use the following command - 
```
docker compose up carla
```
In another window, use the following command:
```
docker compose up carla_ros_bridge
```
If everything is configured correctly, the carla_ros_bridge_with_ego_vehicle example should launch. This will spawn a Tesla Model 3 in a seperate window that you can control, and watch update in the main simulation as you control it via ROS.