cmake_minimum_required(VERSION 3.15)

# set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/extern/CMake-codecov/cmake" ${CMAKE_MODULE_PATH})
# set(CMAKE_CXX_COMPILER /usr/bin/x86_64-linux-gnu-g++-9)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -fPIC" ) # -fpic --coverage
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

project( grpc_hello
         VERSION 1.0.0
         DESCRIPTION "GRPC Hello World Project!"
         LANGUAGES CXX
)

# CLANG Tidy
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Release MinSizeRel
set(CMAKE_BUILD_TYPE Debug)

# Disable in-source builds to prevent source tree corruption.
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
  message(FATAL_ERROR "
FATAL: In-source builds are not allowed.
       You should create a separate directory for build files.
")
endif()

set(EXE_NAME
${PROJECT_NAME}
)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

include(include_directories)
include(local)