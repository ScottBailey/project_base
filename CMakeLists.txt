cmake_minimum_required(VERSION 3.25)
project(project_base)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)



option(BUILD_TESTS "Build the tests." Off)
option(BUILD_EXAMPLES "Build the examples." On)



set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/Modules" ${CMAKE_MODULE_PATH})

# Add third party dependencies BEFORE adding wall & werror.
add_subdirectory(third_party)

# Warnings as errors.
include(Modules/common.cmake)

#add_subdirectory()
