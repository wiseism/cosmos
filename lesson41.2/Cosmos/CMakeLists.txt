cmake_minimum_required(VERSION 3.10)
project(CosmosLesson41_2)

message(STATUS "Building Cosmos lesson41.2 using original Makefile")

add_custom_target(cosmos_lesson41_2_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson41.2 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson41_2_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson41.2"
    VERBATIM
)

message(STATUS "Cosmos lesson41.2 build configuration complete")
