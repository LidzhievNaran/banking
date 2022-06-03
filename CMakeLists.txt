
cmake_minimum_required(VERSION 3.21)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(banking)

include_directories(banking)

add_library(banking STATIC
        banking/Account.cpp
        banking/Transaction.cpp)

if(BUILD_TESTS)
    enable_testing()
    add_subdirectory(third-party/gtest)
    add_executable(check tests/test.cpp)
    target_link_libraries(check banking gtest_main)
    add_test(NAME check COMMAND check)
endif()

