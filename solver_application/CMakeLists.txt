cmake_minimum_required(VERSION 3.4)
project(solver_app)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(../solver_lib build_solver_lib)
add_subdirectory(../formatter_ex_lib build_formatter_ex)


add_executable(solver equation.cpp)

target_include_directories(solver PRIVATE ../solver_lib)


target_link_libraries(solver PUBLIC solver_lib formatter_ex)
