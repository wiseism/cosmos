cmake_minimum_required(VERSION 3.10)
project(CosmosLesson33)

message(STATUS "Building Cosmos lesson33 using original Makefile")

add_custom_target(cosmos_lesson33_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson33 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson33_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson33"
    VERBATIM
)

message(STATUS "Cosmos lesson33 build configuration complete")
