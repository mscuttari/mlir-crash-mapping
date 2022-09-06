cmake_minimum_required(VERSION 3.16)
project(CrashMapping)

set(CMAKE_CXX_STANDARD 17)

find_package(LLVM REQUIRED CONFIG)
include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

find_package(MLIR REQUIRED CONFIG)
include_directories(${MLIR_INCLUDE_DIRS})
add_definitions(${MLIR_DEFINITIONS})

list(APPEND CMAKE_MODULE_PATH "${LLVM_CMAKE_DIR}")
list(APPEND CMAKE_MODULE_PATH "${MLIR_CMAKE_DIR}")

include(TableGen)
include(AddLLVM)
include(AddMLIR)

include_directories(${CMAKE_BINARY_DIR})

add_subdirectory(dialect)
add_executable(CrashMapping main.cpp)
target_link_libraries(CrashMapping PUBLIC MLIRIR MLIRArithmeticDialect MLIRTest)
