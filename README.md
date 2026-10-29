# LASER UAV VIO-s

`laser_uav_vio-s` collects the visual-inertial odometry integration used by the LASER UAV System (LUS). OpenVINS combines tracked camera features and IMU measurements with a Multi-State Constraint Kalman Filter (MSCKF).

The collection fetches `laser_open_vins_core`, which contains the LUS launch files and camera/IMU profiles. Its dependencies include OpenVINS and `laser_vins_republisher`, which converts odometry into the frames used by the estimation stack.

## Install and build

From this repository:

```bash
gitman install
```

Gitman stores the integration in `.gitman/` and links it at `ros_packages/laser_open_vins`. The integration has its own manifest for the component repositories. Make the ROS packages available in the workspace and install their declared dependencies before building:

```bash
colcon build --packages-up-to laser_open_vins_core laser_vins_republisher
source install/setup.bash
```

## Run and configure

Choose the profile for your calibrated camera/IMU setup:

```bash
ros2 launch laser_open_vins_core open_vins.launch.py open_vins_params_folder:=rs_244622073910 namespace:=uav1
```

`topic_imu`, `topic_camera0` and `topic_camera1` select the input streams. The profile contains estimator settings, camera intrinsics, camera-to-IMU extrinsics and IMU noise parameters. Use the calibration for the actual sensor; profiles named after different camera serial numbers are not interchangeable.

The OpenVINS launch starts the estimator. Run the republisher and any required IMU filtering separately, or use the integration's simulation session. The estimation manager consumes the republished odometry at `/<UAV_NAME>/vins_republisher/odometry`.

This collection has no node or runtime parameters of its own. See the [integration README](https://github.com/LASER-Robotics/laser_open_vins_core) for launch arguments, configuration and node interfaces.

## Reference

P. Geneva, K. Eckenhoff, W. Lee, Y. Yang and G. Huang, "OpenVINS: A Research Platform for Visual-Inertial Estimation," IEEE International Conference on Robotics and Automation (ICRA), pp. 4666-4672, 2020. DOI: 10.1109/ICRA40945.2020.9196524.
