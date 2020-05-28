cmake_minimum_required(VERSION 3.16)
project(hc128_c_src)

set(CMAKE_CXX_STANDARD 17)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(ERLANG_HOME "/opt/OTP")
find_package(Erlang)

file(GLOB SOURCES src/*.cpp src/*.c)

add_library(hc128_nif SHARED ${SOURCES})

include_directories(src)
target_include_directories(hc128_nif PUBLIC
    "$<BUILD_INTERFACE:${ERLANG_ERTS_INCLUDE_PATH}>"
)