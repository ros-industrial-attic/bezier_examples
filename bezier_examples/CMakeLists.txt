cmake_minimum_required(VERSION 2.8.3)
project(bezier_examples)
add_compile_options(-Wall -Wextra)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS
  bezier
  fanuc_m10ia_moveit_config_melodic
  fanuc_m10ia_support
  moveit_ros_planning_interface
  roscpp
  roslaunch
  rviz_visual_tools
  tf
  tf_conversions
  visualization_msgs
)

################################################
## Declare ROS messages, services and actions ##
################################################

###################################
## catkin specific configuration ##
###################################

catkin_package(
  CATKIN_DEPENDS
  bezier
  fanuc_m10ia_moveit_config_melodic
  fanuc_m10ia_support
  moveit_ros_planning_interface
  roscpp
  roslaunch
  rviz_visual_tools
  tf
  tf_conversions
  visualization_msgs
)

###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
)

# Surfacing example
add_executable(
  ${PROJECT_NAME}_surfacing
  src/surfacing.cpp
)
target_link_libraries(
  ${PROJECT_NAME}_surfacing
  ${catkin_LIBRARIES}
)

# Painting example
add_executable(
  ${PROJECT_NAME}_painting
  src/painting.cpp
)
target_link_libraries(
  ${PROJECT_NAME}_painting
  ${catkin_LIBRARIES}
)

#############
## Install ##
#############

#############
## Testing ##
#############

if (CATKIN_ENABLE_TESTING)
  roslaunch_add_file_check(tests/roslaunch_test.xml)
endif()
