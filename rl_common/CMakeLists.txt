# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(rl_common)
find_package(catkin REQUIRED)
catkin_package(
  INCLUDE_DIRS include
)

## Install
install(DIRECTORY include/rl_common/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

