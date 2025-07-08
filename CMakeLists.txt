# CMakeList.txt : CMake project for day65, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

set(CMAKE_CXX_STANDARD 17)

project("day65") #project name

#include_path
include_directories(inc)

#Add Library
add_library(mylib src/simp_calc.cpp)

#Main Application
add_executable(MyApp src/main.cpp) #output binary and source files
target_link_libraries(MyApp mylib)

#Unit Test
enable_testing()
#add_executable(MyTests tests/test_add01.cpp)
#target_link_libraries(MyTests mylib)
#add_test(NAME RunMyTests COMMAND MyTests)

macro(add_calc_test name)
add_executable(${name} tests/${name}.cpp)
target_link_libraries(${name} mylib)
add_test(NAME ${name} COMMAND ${name})
endmacro()

#Add test Cases
add_calc_test(test_add01)