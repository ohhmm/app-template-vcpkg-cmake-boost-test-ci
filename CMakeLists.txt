cmake_minimum_required(VERSION 3.15)

project(MinimalVcpkgExample)

# Set C++ standard
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Enable vcpkg integration
if(NOT DEFINED CMAKE_TOOLCHAIN_FILE)
  message(ERROR "set CMAKE_TOOLCHAIN_FILE to vcpkg toolchain file [vcpkg/scripts/buildsystems/vcpkg.cmake]")
endif()

# Find Boost
find_package(Boost REQUIRED COMPONENTS
  filesystem
  multiprecision
  system
  unit_test_framework
)

# Add executable
add_executable(minimal_example main.cpp)

# Link Boost libraries
target_link_libraries(minimal_example
  Boost::filesystem
  Boost::multiprecision
  Boost::system
)

# Add test executable
add_executable(test_example test_main.cpp)

# Link Boost Test and Filesystem libraries
target_link_libraries(test_example
  Boost::unit_test_framework
  Boost::filesystem
  Boost::system
)

