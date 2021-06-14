# cartographer

roscore

rosparam set use_sim_time true
rosparam set -t ./src/cartographer_ros/vlp16-imu-2.urdf robot_description
rosrun robot_state_publisher robot_state_publisher

source devel_isolated/setup.bash
rviz

rosbag play /home/darthshana/Downloads/blue_ch3_2020-02-23-06-07-40.bag --clock -r 1 --topics /blue/velodyne_points /blue/mavros/imu/data

rosrun cartographer_ros cartographer_node -configuration_directory src/cartographer_ros/ -configuration_basename laris_3d.lua points2:=blue/velodyne_points imu:=blue/mavros/imu/data

rosnode info cartographer_node
