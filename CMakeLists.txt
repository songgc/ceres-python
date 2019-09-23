cmake_minimum_required(VERSION 3.0)
project(ceres_python)

set (CMAKE_CXX_STANDARD 14)
add_subdirectory(pybind11)
pybind11_add_module(ceres_python src/bindings.cpp)
target_link_libraries(ceres_python PRIVATE ceres)

find_package(Eigen3 3.2.7 REQUIRED NO_MODULE)
include_directories(${EIGEN_INCLUDE_DIR})

# # Build shared library for ceres-solver
set(BUILD_SHARED_LIBS ON)
add_subdirectory(lib/external/ceres-solver)
include_directories(lib/external/ceres-solver/include)
