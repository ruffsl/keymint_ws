# keymint_ws
scratch workspace for Keymint testing


> Keymint can be used via Docker

``` shell
cd ~/example
docker run -it --rm -v=`pwd`:/root/keymint_ws keymint/keymint_tools:latest
```

> If no Keyment workspace is initialized, create one

``` shell
keymint keystore init --bootstrap=keymint_ros
```

> run these commands from the same directory:

``` shell
keymint keystore create_pkg add_two_ints_client
keymint keystore create_pkg add_two_ints_server
keymint keystore create_pkg hlds_laser_publisher
keymint keystore create_pkg joint_states_publisher
keymint keystore create_pkg launch_ros
keymint keystore create_pkg listener
keymint keystore create_pkg odometry_publisher
keymint keystore create_pkg robot_state_publisher
keymint keystore create_pkg _ros2cli_node_daemon_0
keymint keystore create_pkg rviz
keymint keystore create_pkg scan_publisher
keymint keystore create_pkg talker
keymint keystore create_pkg tf_publisher
keymint keystore create_pkg time_sync
keymint keystore create_pkg turtlebot3_openrc
keymint keystore create_pkg turtlebot3_teleop_key

keymint keystore build_pkg src/add_two_ints_client
keymint keystore build_pkg src/add_two_ints_server
keymint keystore build_pkg src/hlds_laser_publisher
keymint keystore build_pkg src/joint_states_publisher
keymint keystore build_pkg src/launch_ros
keymint keystore build_pkg src/listener
keymint keystore build_pkg src/odometry_publisher
keymint keystore build_pkg src/robot_state_publisher
keymint keystore build_pkg src/_ros2cli_node_daemon_0
keymint keystore build_pkg src/rviz
keymint keystore build_pkg src/scan_publisher
keymint keystore build_pkg src/talker
keymint keystore build_pkg src/tf_publisher
keymint keystore build_pkg src/time_sync
keymint keystore build_pkg src/turtlebot3_openrc
keymint keystore build_pkg src/turtlebot3_teleop_key
exit
```


``` shell
export ROS_SECURITY_ROOT_DIRECTORY=`pwd`/install
export ROS_SECURITY_ENABLE=true
export ROS_SECURITY_STRATEGY=Enforce

ros2 run demo_nodes_cpp talker
ros2 run demo_nodes_cpp listener
```
