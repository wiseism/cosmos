cmake_minimum_required(VERSION 3.10)
project(CosmosLesson41_3)

message(STATUS "Building Cosmos lesson41.3(uefi) using original Makefile")

add_custom_target(cosmos_lesson41_3_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR}
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson41.3(uefi) with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson41_3_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson41.3(uefi)"
    VERBATIM
)

message(STATUS "Cosmos lesson41.3(uefi) build configuration complete")
