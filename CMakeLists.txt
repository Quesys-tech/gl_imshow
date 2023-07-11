# gl_imshow
#
# Copyright (c) 2020 kamino410
#
# This software is published under the Apache License v2.0.
# See https://github.com/kamino410/gl_imshow

cmake_minimum_required(VERSION 3.13)

enable_language(CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(gl_imshow CXX)

add_executable(main_app main.cpp gl_imshow.cpp glsl_program_wrapper.cpp)

find_package(OpenCV REQUIRED)
target_include_directories(main_app PUBLIC ${OpenCV_INCLUDE_DIRS})
target_link_libraries(main_app ${OpenCV_LIBS})

find_package(OpenGL REQUIRED)
target_include_directories(main_app PUBLIC ${OPENGL_INCLUDE_DIR})

find_package(glfw3 REQUIRED)
target_link_libraries(main_app glfw)

find_package(GLEW)
target_link_libraries(main_app GLEW GL X11 GLU)