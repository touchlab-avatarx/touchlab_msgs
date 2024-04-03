cmake_minimum_required(VERSION 3.0.2)
project(touchlab_msgs)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  std_msgs
)

add_message_files(
  FILES
  Float64MultiArrayStamped.msg
)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  StringTrigger.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(
  CATKIN_DEPENDS message_generation std_msgs
)

