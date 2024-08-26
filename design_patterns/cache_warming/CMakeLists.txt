#pragma comment(lib,"pthreadVC3.lib")

# Minimum CMake version required
cmake_minimum_required(VERSION 3.10)

# Project name and version
project(MyBenchmark VERSION 1.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add the source file to the executable
add_executable(mybenchmark mybenchmark.cc)

# Include the benchmark library headers
target_include_directories(mybenchmark PRIVATE /home/benchmark/include)

# Specify the path to the benchmark library
# link_directories(C:/Users/Nikodem/Documents/GitHub/benchmark/build/src/Release)

# Find the benchmark library
find_library(BENCHMARK_LIB benchmark HINTS /home/benchmark/build/src REQUIRED)

# Link the benchmark library and pthread
target_link_libraries(mybenchmark PRIVATE ${BENCHMARK_LIB} pthread)