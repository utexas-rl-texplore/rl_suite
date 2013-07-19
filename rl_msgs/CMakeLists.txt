# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(rl_msgs)

find_package(catkin REQUIRED 
  COMPONENTS
  message_generation
  std_msgs
)

add_message_files(FILES
  RLAction.msg
  RLEnvDescription.msg
  RLEnvSeedExperience.msg
  RLExperimentInfo.msg
  RLStateReward.msg
)

generate_messages(
  DEPENDENCIES std_msgs
)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs
)
