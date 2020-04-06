cmake_minimum_required(VERSION 3.10.0 FATAL_ERROR)

project(samplecpp VERSION "0.1.0" LANGUAGES CXX)

# ---- SOURCES ----

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

set(ENV{MY_SOURCES} "")

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/src)

message(STATUS "MY_SOURCES = " $ENV{MY_SOURCES})

# ---- EXECUTABLE ----

add_executable(samplecpp ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp $ENV{MY_SOURCES})
