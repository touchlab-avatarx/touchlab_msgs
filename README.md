# touchlab_msgs

## Overview

This repository defines custom message types used in ROS2, specifically the `Float64MultiArrayStamped` message, which combines a standard ROS header with a `Float64MultiArray`. This message is useful for transmitting multi-dimensional floating-point data with a timestamp and frame ID.

## Messages

- **Float64MultiArrayStamped**: 
  - **Fields**:
    - `std_msgs/Header header`: Standard ROS message header containing timestamp and frame information.
    - `std_msgs/Float64MultiArray multi_array`: Multi-dimensional array of 64-bit floating point numbers.

The custom message is located in the `msg` folder and can be used to transmit stamped multi-dimensional data in a variety of robotic and sensor applications.

## CMake Configuration

The `CMakeLists.txt` file is configured to build the custom message for ROS2 using `ament` and `rosidl_default_generators`. 

### Key Components:

- `rosidl_generate_interfaces`: Used to generate message code from the `.msg` file.
- Dependencies:
  - `ament_cmake`: Required for ROS2 build and package management.
  - `std_msgs`: Provides the `Header` and `Float64MultiArray` messages, which the custom message depends on.
  - `rosidl_default_generators`: Generates necessary message and service interfaces.

## Example Usage

To use the custom message in your ROS2 package:

1. Add the following dependency to your package’s `CMakeLists.txt`:

```cmake
find_package(touchlab_msgs REQUIRED)
```

2. Include the message header in your node:

```cpp
#include "touchlab_msgs/msg/float64_multi_array_stamped.hpp"
```

3. Use it in your publisher or subscriber:

```cpp
auto msg = touchlab_msgs::msg::Float64MultiArrayStamped();
msg.header.stamp = node->get_clock()->now();
msg.multi_array.data = {1.0, 2.0, 3.0};
publisher->publish(msg);
```

## Launch Files

Since this repository primarily contains message definitions, no specific launch files are included. However, you can integrate these messages into any ROS2 node and corresponding launch files as necessary.

## Dependencies

- [std_msgs](https://index.ros.org/p/std_msgs/): Standard messages for ROS2, providing data types like `Header` and `Float64MultiArray`.
- [ament_cmake](https://index.ros.org/p/ament_cmake/): ROS2 build system.
- [rosidl_default_generators](https://index.ros.org/p/rosidl_default_generators/): Used for generating the message interface code.

## Building the Package

To build the package, ensure that you have a ROS2 workspace set up and follow the usual ROS2 build steps:

```bash
source /opt/ros/<distro>/setup.bash
colcon build --packages-select touchlab_msgs
```

This will generate the necessary message files and install the package.
