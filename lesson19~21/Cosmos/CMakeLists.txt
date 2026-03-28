cmake_minimum_required(VERSION 3.10)
project(CosmosLesson19_21)

message(STATUS "Building Cosmos lesson19~21 using original Makefile")

add_custom_target(cosmos_lesson19_21_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson19~21 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson19_21_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson19~21"
    VERBATIM
)

message(STATUS "Cosmos lesson19~21 build configuration complete")
