cmake_minimum_required(VERSION 3.17 FATAL_ERROR)
project(MyProject LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

include(cmake/CPM.cmake)

CPMAddPackage(
  NAME SDL2
  VERSION 2.0.12
  URL https://libsdl.org/release/SDL2-2.0.12.zip
)

if (SDL2_ADDED)
  add_library(SDL2::SDL2 ALIAS SDL2)
endif()

set(ALLOW_DUPLICATE_CUSTOM_TARGETS True )


find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

add_executable(main main.cpp)
target_link_libraries(main SDL2 ${OPENGL_LIBRARIES})
