cmake_minimum_required(VERSION 3.18)
project(uri_parser)

set(CMAKE_CXX_STANDARD 17)

add_library(uri-parser INTERFACE)
target_include_directories(uri-parser INTERFACE .)

include(FetchContent)

FetchContent_Declare(
    Catch2
    GIT_REPOSITORY https://github.com/catchorg/Catch2.git
    GIT_TAG        v3.0.0-preview3
)

FetchContent_MakeAvailable(Catch2)

add_executable(tests tests.cpp)
target_link_libraries(tests PRIVATE Catch2::Catch2WithMain uri-parser)

add_executable(example example.cpp)
target_link_libraries(example uri-parser)