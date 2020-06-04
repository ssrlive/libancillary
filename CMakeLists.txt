
cmake_minimum_required(VERSION 3.4.1)
project(libancillary C)

set(CMAKE_C_STANDARD 11)

set(LIB_ANCILLARY_DIR ${CMAKE_CURRENT_SOURCE_DIR} CACHE INTERNAL "libancillary library path" FORCE)

include_directories(.)

add_library(
        libancillary
        STATIC
        ancillary.h
        fd_recv.c
        fd_send.c
)

option(libancillary_build_test OFF)

if (libancillary_build_test)
    add_executable(
            test_exe
            test.c
    )
    target_link_libraries(
            test_exe
            libancillary
    )
    add_executable(
            evclient
            evclient.c
    )
    target_link_libraries(
            evclient
            libancillary
    )
    add_executable(
            evserver
            evserver.c
    )
    target_link_libraries(
            evserver
            libancillary
    )
endif (libancillary_build_test)