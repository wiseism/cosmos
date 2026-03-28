cmake_minimum_required(VERSION 3.10)
project(CosmosLesson16_18)

message(STATUS "Building Cosmos lesson16~18 using original Makefile")

add_custom_target(cosmos_lesson16_18_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson16~18 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson16_18_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson16~18"
    VERBATIM
)

message(STATUS "Cosmos lesson16~18 build configuration complete")
