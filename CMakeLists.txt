cmake_minimum_required(VERSION 3.20.0)
project(ROCm-mini-nbody VERSION 0.0.0)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_C_STANDARD 99)

include_directories(./hip)
include_directories(./include)

file(GLOB_RECURSE SRC_FILES ./mic/*.c)

add_executable(${PROJECT_NAME} ${SRC_FILES})
