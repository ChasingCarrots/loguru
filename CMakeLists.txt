cmake_minimum_required(VERSION 3.5)
project(loguru)

option(USE_FMTLIB "Use the fmt library for formatting" OFF)

add_library(loguru loguru.cpp loguru.hpp)
target_include_directories(loguru PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_features(loguru PUBLIC cxx_std_11)
if(USE_FMTLIB)
    target_compile_definitions(loguru PUBLIC LOGURU_USE_FMTLIB=1)
    target_link_libraries(loguru PUBLIC fmt)
endif()

