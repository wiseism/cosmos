cmake_minimum_required(VERSION 3.10)
project(CosmosLesson12)

message(STATUS "Building Cosmos lesson12 using original Makefile")

add_custom_target(cosmos_lesson12_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson12 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson12_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson12"
    VERBATIM
)

message(STATUS "Cosmos lesson12 build configuration complete")
