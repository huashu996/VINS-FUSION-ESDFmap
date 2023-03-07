# VINS-FUSION-ESDF
一种用于视觉实施定位并建图的算法，VINS+FIESTA
# 环境配置
ubuntu18.04
ROS
pcl 1.7
opencv3
ceres-solver-1.14.0
- ROS
``
sudo apt-get install ros-melodic-cv-bridge ros-melodic-tf ros-melodic-message-filters ros-melodic-image-transport ros-melodic-octomap*
``
- Ceres
``
sudo apt-get install liblapack-dev libsuitesparse-dev libcxsparse3 libgflags-dev libgoogle-glog-dev libeigen3-dev libgtest-dev
git clone https://github.com/ceres-solver/ceres-solver.git
cd ceres-solver/
mkdir build
cd build
cmake ..
make
sudo make install
``
- 安装代码
``
sudo mkdir vins-fusion-esdfmap/src
cd vins-fusion-esdfmap/src
git clone git@github.com:huashu996/VINS-FUSION-ESDFmap.git
cd ..
catkin_make
source devel/setup.bash
``
# 运行
- 单目
``
roslaunch realsense2_camera rs_camera_vins.launch 
roslaunch vins vins_rviz.launch 
rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion-ESDF/config/realsense_d435i/realsense_d435i_config.yaml
roslaunch fiesta D435.launch
``
- 双目
``
roslaunch realsense2_camera rs_camera_vins.launch 
roslaunch vins vins_rviz.launch 
rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion-ESDF/config/realsense_d435i/realsense_stereo_imu_config.yaml
roslaunch fiesta D435.launch
``
