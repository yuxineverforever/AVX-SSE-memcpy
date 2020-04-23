CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

set(CMAKE_C_COMPILER "/usr/bin/gcc-8")
set(CMAKE_VERBOSE_MAKEFILE ON)

project(main)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -ffreestanding -march=skylake -mavx2 -O3 -fpie -fomit-frame-pointer -fno-common -fno-zero-initialized-in-bss -fno-exceptions -fno-unwind-tables -fno-asynchronous-unwind-tables -fno-stack-protector -fno-stack-check -fno-strict-aliasing -fno-merge-all-constants -fno-merge-constants -mno-stack-arg-probe -m64 -mno-red-zone -maccumulate-outgoing-args --std=gnu11 -g3 -Wall -Wextra -Wdouble-promotion -Wpedantic -fmessage-length=0 -ffunction-sections -MMD -MP")


add_library(memcmp memcmp.c)
add_library(memmove memmove.c)
add_library(memset memset.c)
add_library(memcpy memcpy.c)

add_executable(main main.c)
set_target_properties(main PROPERTIES COMPILE_FLAGS "-save-temps")

target_link_libraries(main memcpy)
target_link_libraries(main memset)
target_link_libraries(main memcmp)
target_link_libraries(main memmove)


