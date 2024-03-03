cmake_minimum_required(VERSION 3.14)
set(CXX_STANDARD 17)
project(my-project)

include_directories(
        ${PROJECT_SOURCE_DIR}/src
        ${PROJECT_SOURCE_DIR}/include
)
add_subdirectory(libraries/googletest)
file(GLOB all_SRCS
        "${PROJECT_SOURCE_DIR}/include/*.h"
        "${PROJECT_SOURCE_DIR}/src/*.cpp"
)

message(1..................START)
message("${all_SRCS}")
message(1..................END)

file(GLOB all_SRCS "minus.h" "plus.h" "mult.h" "meta.h" "main.cpp")

message(2..................START)
message("${all_SRCS}")
message(2..................END)

option(MATCH_TESTS "build tests (or no)" OFF)

if (MATCH_TESTS)
        # add_library(example_google_tests ${PROJECT_SOURCE_DIR}/libraries/googletest)
        enable_testing()
        add_subdirectory(tests)
endif()


add_executable(app ${all_SRCS})
# add_executable(app ${PROJECT_SOURCE_DIR}/libraries/googletest)
