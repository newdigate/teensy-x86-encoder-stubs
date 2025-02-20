cmake_minimum_required(VERSION 3.10)
project(teensy_x86_encoder_examples_basic C CXX)

set(CMAKE_CXX_STANDARD 17)

include_directories(../../src)

add_executable(encoder_basic basic.cpp)

target_link_libraries(encoder_basic teensy_x86_stubs)
