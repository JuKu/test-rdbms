cmake_minimum_required(VERSION VERSION 3.0)
project(test-rdbms)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BINARY_DIR build)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

include_directories( ${MY_SOURCE_DIR}/src )

find_package(Boost)
IF (Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIR})
endif()

set (Boost_USE_STATIC_LIBS OFF) # enable dynamic linking
set (Boost_USE_MULTITHREAD ON)  # enable multithreading
find_package (Boost COMPONENTS REQUIRED chrono filesystem)

add_executable(test-rdbms src/main/main.cpp)

#If you want to build a library instead, you can use the add_library() command:
#add_library (my_library STATIC|SHARED|MODULE my_source.cpp)