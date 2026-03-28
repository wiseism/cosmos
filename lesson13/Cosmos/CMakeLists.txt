cmake_minimum_required(VERSION 3.10)
project(CosmosLesson13)

message(STATUS "Building Cosmos lesson13 using original Makefile")

add_custom_target(cosmos_lesson13_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson13 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson13_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson13"
    VERBATIM
)

message(STATUS "Cosmos lesson13 build configuration complete")
