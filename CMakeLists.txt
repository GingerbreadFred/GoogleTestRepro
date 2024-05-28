cmake_minimum_required(VERSION 3.5)

project(HelloWorldTest)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/f8d7d77c06936315286eb55f8de22cd23c188571.zip
)

set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(HelloWorld 
    src/HelloWorld.cpp
)

target_link_libraries(HelloWorld GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(HelloWorld)
