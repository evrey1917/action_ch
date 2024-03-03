cmake_minimum_required(VERSION 3.14)
set(CXX_STANDARD 17)
project(my-project)

include_directories(
        ${PROJECT_SOURCE_DIR}/src
        ${PROJECT_SOURCE_DIR}/include
)
add_subdirectory(libraries/googletest)

option(MATCH_TESTS "build tests (or no)" ON)

if (MATCH_TESTS)
        add_library(example_google_tests "${PROJECT_SOURCE_DIR}/include/math/minus.h" "${PROJECT_SOURCE_DIR}/include/math/plus.h" "${PROJECT_SOURCE_DIR}/include/math/mul.h" "${PROJECT_SOURCE_DIR}/include/meta/meta.h" "${PROJECT_SOURCE_DIR}/src/main.cpp")
        enable_testing()
        add_subdirectory(tests)
endif()


add_executable(app "${PROJECT_SOURCE_DIR}/include/math/minus.h" "${PROJECT_SOURCE_DIR}/include/math/plus.h" "${PROJECT_SOURCE_DIR}/include/math/mul.h" "${PROJECT_SOURCE_DIR}/include/meta/meta.h" "${PROJECT_SOURCE_DIR}/src/main.cpp")
