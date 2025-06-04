cmake_minimum_required(VERSION 3.4)
project(my_project)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(formatter STATIC formatter_lib/formatter.cpp)
target_include_directories(formatter PUBLIC formatter_lib)

add_library(formatter_ex STATIC formatter_ex_lib/formatter_ex.cpp)
target_include_directories(formatter_ex PUBLIC formatter_ex_lib)
target_link_libraries(formatter_ex PUBLIC formatter)

add_library(solver_lib STATIC solver_lib/solver.cpp)
target_include_directories(solver_lib PUBLIC solver_lib)

add_executable(hello_world hello_world_application/hello_world.cpp)
target_link_libraries(hello_world PUBLIC formatter_ex)

add_executable(solver solver_application/equation.cpp)
target_link_libraries(solver PUBLIC solver_lib formatter_ex)
