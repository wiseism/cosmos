cmake_minimum_required(VERSION 3.10)
project(CosmosLesson28_29)

message(STATUS "Building Cosmos lesson28~29 using original Makefile")

add_custom_target(cosmos_lesson28_29_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson28~29 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson28_29_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson28~29"
    VERBATIM
)

message(STATUS "Cosmos lesson28~29 build configuration complete")
