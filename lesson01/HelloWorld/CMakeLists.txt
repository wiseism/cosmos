cmake_minimum_required(VERSION 3.10)
project(HelloWorld C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_executable(HelloWorld HelloWorld.c)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(HelloWorld PRIVATE -g -O0)
else()
    target_compile_options(HelloWorld PRIVATE -O2)
endif()
