cmake_minimum_required(VERSION 2.8)

project(hoge CXX)

set(EXTERNAL_INSTALL_LOCATION ${CMAKE_BINARY_DIR}/external)

set(CMAKE_CXX_FLAGS "-std=c++14 -Wall")

include_directories(include)

add_subdirectory(src)
if(NOT without-test)
    enable_testing()
    find_package(Git)
    if(NOT GIT_FOUND)
        message(FATAL_ERROR "git is not found.")
    endif()
    include(cmake/gtest.cmake)
    add_subdirectory(test)
endif()

