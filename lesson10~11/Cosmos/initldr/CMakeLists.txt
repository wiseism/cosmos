cmake_minimum_required(VERSION 3.10)
project(InitLdr C ASM)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

find_program(NASM nasm)
if(NOT NASM)
    message(FATAL_ERROR "nasm not found. Please install nasm: sudo apt install nasm")
endif()

set(ASM_FLAGS -f elf -w-orphan-labels)
set(C_FLAGS -c -Os -std=c99 -m32 -Wall -Wshadow -W -Wconversion -Wno-sign-conversion -fno-stack-protector -fomit-frame-pointer -fno-builtin -fno-common -ffreestanding -Wno-unused-parameter -Wunused-variable)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

set(LDRKRL_SOURCES
    ldrkrl/bstartparm.c
    ldrkrl/chkcpmm.c
    ldrkrl/fs.c
    ldrkrl/graph.c
    ldrkrl/inithead.c
    ldrkrl/ldrkrlentry.c
    ldrkrl/vgastr.c
    ldrkrl/imginithead.asm
    ldrkrl/ldrkrl32.asm
    ldrkrl/realintsve.asm
)

set(OBJ_FILES)

foreach(src ${LDRKRL_SOURCES})
    get_filename_component(ext ${src} EXT)
    get_filename_component(name ${src} NAME_WE)
    set(obj ${CMAKE_CURRENT_BINARY_DIR}/${name}.o)
    
    if(ext STREQUAL ".asm")
        add_custom_command(
            OUTPUT ${obj}
            COMMAND ${NASM} ${ASM_FLAGS} -I${CMAKE_CURRENT_SOURCE_DIR}/include -o ${obj} ${CMAKE_CURRENT_SOURCE_DIR}/${src}
            DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/${src}
            VERBATIM
        )
    elseif(ext STREQUAL ".c")
        add_custom_command(
            OUTPUT ${obj}
            COMMAND ${CMAKE_C_COMPILER} ${C_FLAGS} -I${CMAKE_CURRENT_SOURCE_DIR}/include -o ${obj} ${CMAKE_CURRENT_SOURCE_DIR}/${src}
            DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/${src}
            VERBATIM
        )
    endif()
    
    list(APPEND OBJ_FILES ${obj})
endforeach()

add_custom_target(InitLdr ALL DEPENDS ${OBJ_FILES})

message(STATUS "InitLdr build configuration complete")
