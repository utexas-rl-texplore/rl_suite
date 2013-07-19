# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(rl_experiment)
find_package(catkin REQUIRED COMPONENTS rl_agent rl_common rl_env roscpp std_msgs tf)

catkin_package(
  CATKIN_DEPENDS rl_agent rl_common rl_env roscpp std_msgs tf
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(experiment
  src/rl.cc
)
target_link_libraries(experiment 
  ${catkin_LIBRARIES}
)

install (TARGETS
  experiment
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
