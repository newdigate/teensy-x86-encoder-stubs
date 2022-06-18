cmake_minimum_required(VERSION 3.5)
project(teensy_x86_encoder_stubs C CXX)
set(teensy_x86_encoder_stubs_VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 14)

set(INCLUDE_INSTALL_DIR ${CMAKE_INSTALL_PREFIX}/include/teensy_x86_encoder_stubs/)
set(LIB_INSTALL_DIR ${CMAKE_INSTALL_PREFIX}/lib/teensy_x86_encoder_stubs )

find_package(teensy_x86_stubs)
include_directories(${teensy_x86_stubs_INCLUDE_DIR})

set(HEADER_FILES
		Encoder.h)

add_library(teensy_x86_encoder_stubs INTERFACE ${HEADER_FILES})

set_target_properties(teensy_x86_encoder_stubs PROPERTIES PUBLIC_HEADER "${HEADER_FILES}")

include(CMakePackageConfigHelpers)
configure_package_config_file(../cmake/teensy_x86_encoder_stubs.cmake.in
		${CMAKE_CURRENT_BINARY_DIR}/teensy_x86_encoder_stubsConfig.cmake
		INSTALL_DESTINATION ${LIB_INSTALL_DIR}/teensy_x86_encoder_stubs/cmake
		PATH_VARS)

write_basic_package_version_file(
		${CMAKE_CURRENT_BINARY_DIR}/teensy_x86_encoder_stubsConfigVersion.cmake
		VERSION ${teensy_x86_encoder_stubs_VERSION}
		COMPATIBILITY SameMajorVersion )

install(TARGETS teensy_x86_encoder_stubs DESTINATION
		LIBRARY DESTINATION ${LIB_INSTALL_DIR}
		ARCHIVE DESTINATION ${LIB_INSTALL_DIR}
		PUBLIC_HEADER DESTINATION "include/teensy_x86_encoder_stubs"
		)

install(FILES
		${UTILITY_HEADER_FILES}
		DESTINATION "include/teensy_x86_encoder_stubs/utility" )

install(FILES
		${CMAKE_CURRENT_BINARY_DIR}/teensy_x86_encoder_stubsConfig.cmake
		${CMAKE_CURRENT_BINARY_DIR}/teensy_x86_encoder_stubsConfigVersion.cmake
		../cmake/uninstall.cmake
		DESTINATION "lib/cmake/teensy_x86_encoder_stubs" )

##
# copied from: https://gist.github.com/royvandam/3033428
# Add uninstall target
# Requirements: Copy the uninstall.cmake file to the appropriate CMAKE_MODULE_PATH.
#

add_custom_target(uninstall
		"${CMAKE_COMMAND}" -P "../cmake/uninstall.cmake"
		)