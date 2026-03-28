cmake_minimum_required(VERSION 3.10)
project(CosmosLesson41_1)

message(STATUS "Building Cosmos lesson41.1 using original Makefile")

add_custom_target(cosmos_lesson41_1_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson41.1 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson41_1_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson41.1"
    VERBATIM
)

message(STATUS "Cosmos lesson41.1 build configuration complete")
