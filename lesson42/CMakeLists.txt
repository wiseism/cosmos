cmake_minimum_required(VERSION 3.10)
project(Lesson42 C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_executable(cpus main.c)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(cpus PRIVATE -g -O0)
else()
    target_compile_options(cpus PRIVATE -O2)
endif()

message(STATUS "Lesson42 build configuration complete")
