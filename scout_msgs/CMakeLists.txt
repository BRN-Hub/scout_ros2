cmake_minimum_required(VERSION 3.5)
project(scout_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)

set(msg_file
"msg/ScoutActuatorState.msg"
"msg/ScoutBmsStatus.msg"
"msg/ScoutLightCmd.msg"
"msg/ScoutLightState.msg"
"msg/ScoutRCState.msg"
"msg/ScoutStatus.msg"
)

# set(srv_file
# "srv/ActuatorStateCheck.srv"
# "srv/LightStateCheck.srv"
# "srv/RcStateCheck.srv"
# "srv/SystemStateCheck.srv"
# )

rosidl_generate_interfaces(${PROJECT_NAME}
    ${msg_file} # ${srv_file}
  DEPENDENCIES 
    builtin_interfaces std_msgs)
  
if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_export_dependencies(rosidl_default_runtime)

ament_package()