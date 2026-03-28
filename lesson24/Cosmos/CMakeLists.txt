cmake_minimum_required(VERSION 3.10)
project(CosmosLesson24)

message(STATUS "Building Cosmos lesson24 using original Makefile")

add_custom_target(cosmos_lesson24_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson24 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson24_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson24"
    VERBATIM
)

message(STATUS "Cosmos lesson24 build configuration complete")
