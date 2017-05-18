cmake_minimum_required(VERSION 2.8.3)
project(edgmapping)

set(CMAKE_CXX_FLAGS "-march=native -O2 -std=c++11 -fopenmp")
set(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS   "-march=native -O2 -fopenmp")
set(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "-march=native -O2 -fopenmp")
set(CMAKE_EXE_LINKER_FLAGS "-march=native -O2 -fopenmp")

find_package(catkin REQUIRED COMPONENTS
  message_filters
  roscpp
  sensor_msgs
  geometry_msgs
  tf
  pcl_ros
  pcl_conversions
  pcl_msgs
)
find_package(cmake_modules REQUIRED)
find_package(Eigen REQUIRED)
add_definitions(${EIGEN_DEFINITIONS})

catkin_package(
  CATKIN_DEPENDS 
    message_filters 
    roscpp 
    sensor_msgs
    tf
    pcl_ros
    pcl_conversions
    pcl_msgs
  INCLUDE_DIRS include
)

include_directories(
  include/edgmapping
  include/edgmapping/motion_update
  include/edgmapping/sensor_update
  include/edgmapping/map
  include/edgmapping/utils
  include/edgmapping/particlefilter
  ${catkin_INCLUDE_DIRS} include
  ${Eigen_INCLUDE_DIRS}
)

add_executable(edgmapping
  src/edgmapping_node.cpp
  src/edgmapping/motion_update/motionmodel.cpp
  src/edgmapping/sensor_update/smmap.cpp
  src/edgmapping/sensor_update/scanmatcher.cpp
  src/edgmapping/utils/stat.cpp
)

target_link_libraries(edgmapping
  ${catkin_LIBRARIES}
)
