# patterns-for-low-latency-applications

This repository contains a collection of C++ design patterns focused on optimizing performance for low-latency applications. The patterns are implemented in individual folders, each containing a `CMakeLists.txt` file for building the corresponding benchmark. The benchmarks use the Google Benchmark library.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Setting Up the Environment](#setting-up-the-environment)
- [Building the Project](#building-the-project)
- [Running the Benchmarks](#running-the-benchmarks)
- [Viewing the Results](#viewing-the-results)

## Prerequisites
Before you begin, ensure you have the following installed on your machine:
- Docker 27.1.2
- Docker-Compose 1.29.2
- Git
- C++ 20
- CMake 3.28.3
- Make 4.3

## Setting Up the Environment

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/nczarli/patterns-for-low-latency-applications.git
    cd patterns-for-low-latency-applications
    ```

2. **Launch Docker Compose**:
    The project uses a Docker container to ensure that all dependencies are correctly set up.
    ```bash
    docker-compose up
    ```

    This command runs a Docker container that:
    - Checks out the Google Benchmark library.
    - Builds the library.
    - Clones the design patterns repository.
    - Builds the individual benchmarks.

## Building the Project

To build the project for a specific design pattern:

1. Navigate to the design pattern's folder. For example, to build the `cache_warming` pattern:
    ```bash
    cd design_patterns/cache_warming
    ```

2. Build the pattern using CMake:
    ```bash
    mkdir build
    cd build
    cmake ..
    make
    ```

The executable for the benchmark will be generated in the `build` directory.

## Running the Benchmarks

To run the benchmark for a specific pattern, use the following command within the pattern's `build` directory:
```bash
./mybenchmark