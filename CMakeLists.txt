cmake_minimum_required(VERSION 3.0)

set(CMAKE_TOOLCHAIN_FILE cmake-avr-toolchain/avr-gcc.toolchain.cmake)
include(cmake-avr-toolchain/avr-gcc.toolchain.cmake)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake-avr-toolchain/Modules/")
project(avr_cross_compile)

find_package(Arduino)

include_directories(${ARDUINO_INCLUDE_DIR})
link_directories(${ARDUINO_LIB_ROOT}) # todo figure out

add_definitions(-DF_CPU=16000000)
add_avr_executable(${PROJECT_NAME} "atmega328p" # arduino nano
    main.c
)
