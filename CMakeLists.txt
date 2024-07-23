cmake_minimum_required(VERSION 3.10.2)

# set the compile output path
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(CMAKE_C_COMPILER "tecocc")
set(CMAKE_CXX_COMPILER "tecocc")

# set cxx to std11 standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project(tecoal)

add_compile_options(-Werror -DUSE_EXPERIMENTAL_SDAA_API)
#add_compile_options(-debug)

set(PROJECT_INCLUDE ${PROJECT_SOURCE_DIR})

include_directories(${PROJECT_INCLUDE})

set(ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR})

# create ual library
add_subdirectory(${ROOT_DIR}/ual)

# create tecoal library
add_subdirectory(${ROOT_DIR}/interface)

# enter the test framework
if(BUILD_TEST)
    add_subdirectory(${ROOT_DIR}/samples)
endif()
