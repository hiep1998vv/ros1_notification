some notification about install ros melodic for raspberry pi

sudo apt-get install -y python3-rosdep python3-rosinstall-generator python3-wstool python3-rosinstall build-essential cmake

rosdep install --from-paths src --ignore-src -y --os=debian:buster
export ROS_OS_OVERRIDE="debian" && rosdep update

rosdep install -y --from-paths src --ignore-src --rosdistro melodic -r --os=debian:buster

# set default python to python3 on raspberry when install ros
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 1

sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic -j2 -DPYTHON_EXECUTABLE=/usr/bin/python3

sudo nano /etc/apt/sources.list.d/ros-latest.list

hmt.japan.2016@gmail.com
Truonghang123

# source list
deb http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian/ buster main contrib non-free rpi

# package ros
deb http://packages.ros.org/ros/ubuntu buster main

# sudo update show
Hit:1 http://archive.raspberrypi.org/debian buster InRelease                   
Hit:2 http://packages.ros.org/ros/ubuntu buster InRelease                      
Hit:3 http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian buster InRelease
Reading package lists... Done


