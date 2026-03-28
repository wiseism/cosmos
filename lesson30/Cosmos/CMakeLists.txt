cmake_minimum_required(VERSION 3.10)
project(CosmosLesson30)

message(STATUS "Building Cosmos lesson30 using original Makefile")

add_custom_target(cosmos_lesson30_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson30 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson30_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson30"
    VERBATIM
)

message(STATUS "Cosmos lesson30 build configuration complete")
