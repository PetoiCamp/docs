---
description: ROS Interface
---

# 🤖 ROS

There's also a [ROS wrapper](https://github.com/PetoiCamp/ros\_opencat) for developpers to easily connect to the [ROS](https://www.ros.org/) environment. It is recommended to use ROS with [Raspberry Pi](raspberry-pi-serial-port-as-an-interface.md).

### Using ROS on Raspberry Pi

Currently, it's recommended to install ROS using docker.

* install docker on Raspberry Pi ([ref](https://phoenixnap.com/kb/docker-on-raspberry-pi))

```bash
sudo apt-get update && sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker pi
# test installation
docker run hello-world
```

* prepare workspace

```bash
mkdir -p workspace/src
cd workspace/src
git clone https://github.com/PetoiCamp/ros_opencat
cd ros_opencat
git submodule init && git submodule update
cd ../../..
```

* run the container

```bash
docker run -v path/to/workspace:/workspace \
-it --rm --privileged --network host --name ros ros:noetic-robot
```

* source files and build inside the container

```bash
cd /workspace
source /opt/ros/noetic/setup.bash
catkin_makbase
source devel/setup.bash
```

* run examples (see [Examples](ros.md#examples) for more)

```bash
rosrun opencat_examples opencat_examples_serial
```

### Using ROS for remote control

Ros is designed with distributed computing in mind. Here's a simple example on how to run nodes on different machines.

* on host machine (usually more powerful than Raspberry Pi)

```bash
# launch server
roscore
```

* run service node on Raspberry Pi

```bash
export ROS_MASTER_URI=http://<Host_IP>:11311/
rosrun opencat_server opencat_service_node
```

* send command from host

```
rosrun opencat_examples opencat_examples_client_cpp
```

### Examples

* using serial library

```bash
rosrun opencat_examples opencat_examples_serial
```

* using ROS service

```bash
# start core
roscore
# start service server
rosrun opencat_server opencat_service_node
# examples using oppencat ros service in C++
rosrun opencat_examples opencat_examples_client_cpp
# examples using opencat ros service in python
rosrun opencat_examples opencat_examples_client_py
```
