cmake_minimum_required(VERSION 2.8.3)
project(px4ros)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  mavros
  mavros_extras
  geometry_msgs
  angles

  message_generation
)

add_message_files(FILES gpsPosition.msg)

generate_messages()


catkin_package(
  CATKIN_DEPENDS message_runtime
)


include_directories(
  ${catkin_INCLUDE_DIRS}
)


add_executable(px4ros src/px4_getpoint_node.cpp)


target_link_libraries(px4ros
   ${catkin_LIBRARIES}
 )

