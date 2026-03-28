cmake_minimum_required(VERSION 3.10)
project(CosmosLesson37)

message(STATUS "Building Cosmos lesson37 using original Makefile")

add_custom_target(cosmos_lesson37_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson37 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson37_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson37"
    VERBATIM
)

message(STATUS "Cosmos lesson37 build configuration complete")
