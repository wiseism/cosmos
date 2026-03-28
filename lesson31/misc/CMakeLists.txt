cmake_minimum_required(VERSION 3.10)
project(MiscDrv C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_executable(app app.c)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(app PRIVATE -g -O0)
else()
    target_compile_options(app PRIVATE -O2)
endif()

message(STATUS "Note: miscdrv.c is a kernel module and must be built with kernel build system")
message(STATUS "To build the kernel module, run: cd lesson31/misc && make")
message(STATUS "Lesson31/misc build configuration complete")
