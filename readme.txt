some notification about install ros melodic for raspberry pi

sudo apt-get install -y python3-rosdep python3-rosinstall-generator python3-wstool python3-rosinstall build-essential cmake

rosdep install --from-paths src --ignore-src -y --os=debian:buster
export ROS_OS_OVERRIDE="debian" && rosdep update

rosdep install -y --from-paths src --ignore-src --rosdistro melodic -r --os=debian:buster
sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic -j2 -DPYTHON_EXECUTABLE=/usr/bin/python3

sudo nano /etc/apt/sources.list.d/ros-latest.list
