cmake_minimum_required(VERSION 3.20.0)
project(ROCm-mini-nbody VERSION 0.0.0 LANGUAGES CXX C)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_C_STANDARD 99)

# Include directories
include_directories(./include)

# Find HIP
find_package(hip QUIET)

# CPU version (original)
# add_executable(nbody-cpu nbody.c)

# MIC versions (if needed)
# add_executable(nbody-mic-soa mic/nbody-soa.c)
# add_executable(nbody-mic-block mic/nbody-block.c)
# add_executable(nbody-mic-align mic/nbody-align.c)

# HIP versions (for ROCm)
if(hip_FOUND)
    # HIP original version
    add_executable(nbody-hip-orig hip/nbody-orig.hip)
    target_link_libraries(nbody-hip-orig hip::device)

    # HIP SOA version
    add_executable(nbody-hip-soa hip/nbody-soa.hip)
    target_link_libraries(nbody-hip-soa hip::device)

    # HIP block version
    add_executable(nbody-hip-block hip/nbody-block.hip)
    target_link_libraries(nbody-hip-block hip::device)

    # HIP unroll version
    add_executable(nbody-hip-unroll hip/nbody-unroll.hip)
    target_link_libraries(nbody-hip-unroll hip::device)
else()
    message(STATUS "HIP not found. Skipping HIP targets.")
endif()
