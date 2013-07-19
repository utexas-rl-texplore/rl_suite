# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(rl_agent)
find_package(catkin REQUIRED COMPONENTS std_msgs roscpp rl_msgs tf rl_common)

catkin_package(
  CATKIN_DEPENDS std_msgs roscpp rl_msgs tf rl_common
  INCLUDE_DIRS include
  LIBRARIES agentlib
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_library(agentlib
  src/Agent/DiscretizationAgent.cc 
  src/Agent/QLearner.cc
  src/Agent/ModelBasedAgent.cc
  src/Agent/SavedPolicy.cc
  src/Agent/Dyna.cc
  src/Agent/Sarsa.cc
  src/Models/FactoredModel.cc
  src/Models/M5Tree.cc
  src/Models/LinearSplitsTree.cc
  src/Models/C45Tree.cc
  src/Models/Stump.cc
  src/Models/MultipleClassifiers.cc
  src/Models/ExplorationModel.cc
  src/Models/RMaxModel.cc 
  src/Models/SepPlanExplore.cc 
  src/Planners/ValueIteration.cc
  src/Planners/PolicyIteration.cc
  src/Planners/PrioritizedSweeping.cc 
  src/Planners/ETUCT.cc
  src/Planners/PO_ParallelETUCT.cc
  src/Planners/ParallelETUCT.cc
  src/Planners/PO_ETUCT.cc
  src/Planners/MBS.cc
  src/newmat/newmat1.cc 
  src/newmat/newmat2.cc 
  src/newmat/newmat3.cc 
  src/newmat/newmat4.cc 
  src/newmat/newmat5.cc 
  src/newmat/newmat6.cc 
  src/newmat/newmat7.cc 
  src/newmat/newmat8.cc 
  src/newmat/newmatex.cc 
  src/newmat/bandmat.cc 
  src/newmat/submat.cc 
  src/newmat/myexcept.cc 
  src/newmat/cholesky.cc 
  src/newmat/evalue.cc 
  src/newmat/fft.cc 
  src/newmat/hholder.cc 
  src/newmat/jacobi.cc 
  src/newmat/newfft.cc 
  src/newmat/sort.cc 
  src/newmat/svd.cc 
  src/newmat/newmatrm.cc 
  src/newmat/newmat9.cc
)

add_executable(agent
  src/agent.cpp
)
target_link_libraries(agent 
  agentlib
  ${catkin_LIBRARIES}
)

# install targets
install (DIRECTORY include/rl_agent/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install (TARGETS
  agent
  agentlib
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
