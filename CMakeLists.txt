cmake_minimum_required(VERSION 3.10.0 FATAL_ERROR)
project(samplecpp VERSION "0.1.0" LANGUAGES CXX)

# ---- OPTIONS ----

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

if(("${CMAKE_CXX_COMPILER_ID}" MATCHES "GNU") OR ("${CMAKE_CXX_COMPILER_ID}" MATCHES "Clang"))
    add_compile_options(-Wall)
    add_compile_options(-Wextra)
    add_compile_options(-Wpedantic)
elseif(DEFINED MSVC)
    add_compile_options(/W4)
endif()

# ---- EXECUTABLE ----

add_executable(samplecpp src/main.cpp)

# ---- SOURCES ----
include_directories(${CMAKE_SOURCE_DIR}/src)
set(
    MY_SOURCES
    src/something/a.cpp
    src/something/b.cpp
)
target_sources(samplecpp PRIVATE ${MY_SOURCES})
