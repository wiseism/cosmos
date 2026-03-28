cmake_minimum_required(VERSION 3.10)
project(CosmosLesson25_26)

message(STATUS "Building Cosmos lesson25~26 using original Makefile")

add_custom_target(cosmos_lesson25_26_all
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} -f Makefile.x86
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Building Cosmos lesson25~26 with Makefile"
    VERBATIM
)

add_custom_target(cosmos_lesson25_26_clean
    COMMAND make -C ${CMAKE_CURRENT_SOURCE_DIR} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Cleaning Cosmos lesson25~26"
    VERBATIM
)

message(STATUS "Cosmos lesson25~26 build configuration complete")
