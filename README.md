# LASER UAV VIO-s

This package aggregates all external Visual Inertial Odometry (VIO) algorithms integrated for use in the system.

## Integrated Algorithms

### OpenVINS
-   **Description:** OpenVINS is a comprehensive and versatile research platform for visual-inertial estimation. It employs a filter-based approach (Multi-State Constraint Kalman Filter - MSCKF) to tightly fuse visual feature tracks from cameras with high-frequency IMU data. Key features include on-manifold sliding window filtering, online camera-IMU extrinsic calibration, and time offset estimation, making it suitable for accurate state estimation on resource-constrained UAV hardware.

-   **Reference:**
    P. Geneva, K. Eckenhoff, W. Lee, Y. Yang and G. Huang, "OpenVINS: A Research Platform for Visual-Inertial Estimation," 2020 IEEE International Conference on Robotics and Automation (ICRA), Paris, France, 2020, pp. 4666-4672, doi: 10.1109/ICRA40945.2020.9196524.
