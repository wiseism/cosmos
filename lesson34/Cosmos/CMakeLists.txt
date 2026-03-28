cmake_minimum_required(VERSION 3.10)
project(CosmosLesson34)

message(STATUS "Building Cosmos lesson34 using original Makefile")

add_custom_target(cosmos_lesson34_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson34 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson34_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson34"
    VERBATIM
)

message(STATUS "Cosmos lesson34 build configuration complete")
