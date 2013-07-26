# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(rl_env)
find_package(catkin REQUIRED COMPONENTS rl_common rl_msgs roscpp std_msgs tf)

catkin_package(
  CATKIN_DEPENDS rl_common rl_msgs roscpp std_msgs tf
  INCLUDE_DIRS include
  LIBRARIES envlib
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_library(envlib
  src/Env/tworooms.cc
  src/Env/taxi.cc
  src/Env/MountainCar.cc
  src/Env/FuelRooms.cc
  src/Env/CartPole.cc
  src/Env/fourrooms.cc
  src/Env/RobotCarVel.cc
  src/Env/energyrooms.cc
  src/Env/gridworld.cc
  src/Env/stocks.cc
  src/Env/LightWorld.cc
)

add_executable(env
  src/env.cpp
)
target_link_libraries(env 
  envlib
  ${catkin_LIBRARIES}
)

# install targets
install (DIRECTORY include/rl_env/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install (TARGETS
  env
  envlib
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
