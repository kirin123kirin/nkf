cmake_minimum_required(VERSION 3.15)

project(nkf LANGUAGES CXX C)

add_executable(nkf
    ${CMAKE_CURRENT_SOURCE_DIR}/nkf.c
    ${CMAKE_CURRENT_SOURCE_DIR}/utf8tbl.c
)

add_library(nkf32 SHARED
    ${CMAKE_CURRENT_SOURCE_DIR}/libnkf.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/nkf32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/utf8tbl.c
)

add_library(nkf32static STATIC
    ${CMAKE_CURRENT_SOURCE_DIR}/libnkf.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/nkf32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/utf8tbl.c
)

install(
    TARGETS nkf nkf32static
    RUNTIME    DESTINATION bin
    LIBRARY    DESTINATION lib
)

install(
    TARGETS nkf32
    RUNTIME    DESTINATION lib ## for windows dll
    LIBRARY    DESTINATION lib
)

install(
    FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/libnkf.h
    DESTINATION lib
)
