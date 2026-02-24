cmake_minimum_required(VERSION 3.8)
project(ros2_lifecycle)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_lifecycle REQUIRED)
find_package(std_msgs REQUIRED)

# Add the executable target named 'lifecycle_sensor'
add_executable(lifecycle_sensor src/lifecycle_sensor.cpp)

# Add dependencies for rclcpp, rclcpp_lifecycle, std_msgs
ament_target_dependencies(lifecycle_sensor rclcpp rclcpp_lifecycle std_msgs)

# Install the target
install(TARGETS
  lifecycle_sensor
  DESTINATION lib/${PROJECT_NAME})

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()