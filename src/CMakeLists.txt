cmake_minimum_required(VERSION 3.5)
project(teensy_x86_encoder_stubs C CXX)
set(teensy_x86_encoder_stubs_VERSION 1.0.1)

set(CMAKE_CXX_STANDARD 14)

find_package(teensy_x86_stubs)
include_directories(${teensy_x86_stubs_INCLUDE_DIR})

set(HEADER_FILES
		Encoder.h)

add_library(teensy_x86_encoder_stubs INTERFACE ${HEADER_FILES})