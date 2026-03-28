cmake_minimum_required(VERSION 3.10)
project(HelloOS C ASM)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

find_program(NASM nasm)
if(NOT NASM)
    message(FATAL_ERROR "nasm not found. Please install nasm: sudo apt install nasm")
endif()

set(ASM_FLAGS -f elf -w-orphan-labels)
set(C_FLAGS -c -Os -std=c99 -m32 -Wall -Wshadow -W -Wconversion -Wno-sign-conversion -fno-stack-protector -fomit-frame-pointer -fno-builtin -fno-common -ffreestanding -Wno-unused-parameter -Wunused-variable)

set(HELLOOS_OBJS
    ${CMAKE_CURRENT_BINARY_DIR}/entry.o
    ${CMAKE_CURRENT_BINARY_DIR}/main.o
    ${CMAKE_CURRENT_BINARY_DIR}/vgastr.o
)

set(HELLOOS_ELF ${CMAKE_CURRENT_BINARY_DIR}/HelloOS.elf)
set(HELLOOS_BIN ${CMAKE_CURRENT_BINARY_DIR}/HelloOS.bin)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/entry.o
    COMMAND ${NASM} ${ASM_FLAGS} -o ${CMAKE_CURRENT_BINARY_DIR}/entry.o ${CMAKE_CURRENT_SOURCE_DIR}/entry.asm
    DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/entry.asm
    VERBATIM
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/main.o
    COMMAND ${CMAKE_C_COMPILER} ${C_FLAGS} -o ${CMAKE_CURRENT_BINARY_DIR}/main.o ${CMAKE_CURRENT_SOURCE_DIR}/main.c
    DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/main.c
    VERBATIM
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/vgastr.o
    COMMAND ${CMAKE_C_COMPILER} ${C_FLAGS} -o ${CMAKE_CURRENT_BINARY_DIR}/vgastr.o ${CMAKE_CURRENT_SOURCE_DIR}/vgastr.c
    DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/vgastr.c
    VERBATIM
)

add_custom_command(
    OUTPUT ${HELLOOS_ELF}
    COMMAND ${CMAKE_LINKER} -s -static -T ${CMAKE_CURRENT_SOURCE_DIR}/hello.lds -n -o ${HELLOOS_ELF} ${HELLOOS_OBJS}
    DEPENDS ${HELLOOS_OBJS} ${CMAKE_CURRENT_SOURCE_DIR}/hello.lds
    VERBATIM
)

add_custom_command(
    OUTPUT ${HELLOOS_BIN}
    COMMAND ${CMAKE_OBJCOPY} -S -O binary ${HELLOOS_ELF} ${HELLOOS_BIN}
    DEPENDS ${HELLOOS_ELF}
    VERBATIM
)

add_custom_target(HelloOS ALL DEPENDS ${HELLOOS_BIN})

add_custom_target(clean_helloos
    COMMAND ${CMAKE_COMMAND} -E remove -f ${CMAKE_CURRENT_BINARY_DIR}/*.o ${CMAKE_CURRENT_BINARY_DIR}/*.bin ${CMAKE_CURRENT_BINARY_DIR}/*.elf
)
