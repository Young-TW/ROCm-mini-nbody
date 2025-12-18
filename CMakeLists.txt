cmake_minimum_required(VERSION 3.21)
project(ROCm-mini-nbody VERSION 0.0.0 LANGUAGES CXX C)
add_definitions(-D__HIP_PLATFORM_AMD__)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_C_STANDARD 99)

project(ROCm-mini-nbody VERSION 0.0.0 LANGUAGES CXX C HIP)

# Include directories
include_directories(./include)

# Find HIP
set(HIP_COMPILER /opt/rocm/bin/hipcc)
set(CMAKE_HIP_COMPILER /opt/rocm/bin/hipcc)

# CPU version (original)
# add_executable(nbody-cpu nbody.c)

# MIC versions (if needed)
# add_executable(nbody-mic-soa mic/nbody-soa.c)
# add_executable(nbody-mic-block mic/nbody-block.c)
# add_executable(nbody-mic-align mic/nbody-align.c)

# HIP versions (for ROCm)

# HIP original version
add_executable(nbody-hip-orig hip/nbody-orig.hip)

# HIP SOA version
add_executable(nbody-hip-soa hip/nbody-soa.hip)

# HIP block version
add_executable(nbody-hip-block hip/nbody-block.hip)

# HIP unroll version
add_executable(nbody-hip-unroll hip/nbody-unroll.hip)
