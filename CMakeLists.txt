cmake_minimum_required(VERSION 3.13)

set(target "wisdom_hal_extender")
project(${target} C CXX ASM)

add_library(${target} INTERFACE)

target_sources(${target} INTERFACE
	src/modules_weak/radio_weak.c
)

target_include_directories(${target} INTERFACE
	src
	modules
)

if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/modules/radio)
	add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/modules/radio)
	target_link_libraries(${target} INTERFACE whale_radio_module)
endif()
