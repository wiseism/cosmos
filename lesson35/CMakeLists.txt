cmake_minimum_required(VERSION 3.10)
project(Lesson35)

message(STATUS "Note: trfs.c is a kernel module and must be built with kernel build system")
message(STATUS "To build the kernel module, run: cd lesson35 && make")
message(STATUS "Lesson35 build configuration complete")

add_custom_target(lesson35_info
    COMMAND ${CMAKE_COMMAND} -E echo "To build trfs kernel module, run: cd ${CMAKE_CURRENT_SOURCE_DIR} && make"
    COMMENT "Lesson35 information"
    VERBATIM
)
