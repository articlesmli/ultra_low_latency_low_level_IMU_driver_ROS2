# Ultra Low-Latency Low-Level IMU Driver (ROS 2)

A production-grade, deterministic C++ ROS 2 driver designed for high-frequency IMU sensor integration in autonomous systems (such as AUVs and mobile robots).

## Key Production Features

* **Zero-Allocation Loop:** Eliminates dynamic memory allocation inside the high-frequency control loop by pre-allocating message containers once during node initialization.
* **Deterministic Timing:** Executes a reliable 100 Hz (10ms) wall timer loop optimized for real-time control constraints.
* **Robust Error Handling:** Features built-in try-catch blocks and throttled safety logs to prevent node crashes during transient hardware communication faults.
* **Optimized Transport QoS:** Configured with `rclcpp::SensorDataQoS()` profiles to minimize latency and ensure reliable sensor data delivery.

## Installation & Building

1. Clone or place this package inside your ROS 2 workspace source directory:
```bash
cd ~/dev_ws/src
# Ensure your package (auv_drivers_cpp) is located here

```


2. Build the package using `colcon`:
```bash
cd ~/dev_ws
colcon build --packages-select auv_drivers_cpp

```


3. Source your workspace environment:
```bash
source install/setup.bash

```



## Usage

Run the production IMU driver node:

```bash
ros2 run auv_drivers_cpp imu_driver_node

```

In a separate terminal, verify that the raw IMU data is streaming correctly:

```bash
source /opt/ros/humble/setup.bash
source ~/dev_ws/install/setup.bash
ros2 topic echo /sensor/imu/raw

```
