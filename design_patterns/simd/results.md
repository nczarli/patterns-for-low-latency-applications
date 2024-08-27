# SIMD vs. Non-SIMD Array Addition Benchmark Results

This document summarizes the results of benchmarking the performance impact of using SIMD (Single Instruction, Multiple Data) instructions versus traditional scalar operations for array addition in C++.

## What is SIMD?

SIMD (Single Instruction, Multiple Data) is a parallel processing technique that allows a single instruction to operate on multiple data points simultaneously. SIMD is commonly used to speed up processing tasks by leveraging the parallel capabilities of modern processors.

### Key Characteristics:
- **Parallelism**: SIMD operations process multiple data elements in parallel using a single instruction, which can significantly accelerate data processing tasks.
- **Efficiency**: By performing operations on multiple data points at once, SIMD reduces the number of instructions and memory accesses required.
- **Use Cases**: SIMD is ideal for tasks that involve processing large arrays or matrices, such as image processing, scientific computations, and data analytics.

## Benchmark Overview

The benchmark compares two scenarios:

- **Non-SIMD Array Addition** (`BM_ArrayAddition`): Traditional scalar array addition.
- **SIMD Array Addition** (`BM_ArrayAddition_SIMD`): Array addition using SIMD instructions (SSE2).

### Results

| Benchmark                   | Time (ns) | CPU Time (ns) | Iterations |
|-----------------------------|-----------|---------------|------------|
| **BM_ArrayAddition**        | 8,316     | 8,316         | 83,039     |
| **BM_ArrayAddition_SIMD**   | 5,825     | 5,825         | 120,221    |

### Interpretation

- **Non-SIMD Array Addition**:
  - Each operation took approximately **8,316 nanoseconds**.
  - Achieved a total of 83,039 iterations.

- **SIMD Array Addition**:
  - Each operation took approximately **5,825 nanoseconds**.
  - Achieved a total of 120,221 iterations.

### Conclusion

The results demonstrate that SIMD instructions provide a substantial performance improvement over traditional scalar operations for array addition. SIMD operations are significantly faster, as evidenced by the lower execution time and higher number of iterations. This performance boost is due to the parallel processing capabilities of SIMD, which allows multiple data elements to be processed simultaneously.

## Running the Benchmark

To reproduce these results, navigate to the `simd` directory and follow these steps:

1. **Build the Benchmark**:
    ```bash
    mkdir build
    cd build
    cmake ..
    make
    ```

2. **Run the Benchmark**:
    ```bash
    ./mybenchmark
    ```

The results will be displayed in the terminal after the benchmark completes.

## Additional Information

This benchmark is part of a broader set of performance patterns aimed at optimizing low-latency applications. For more details, refer to the main repository.

---

**Note**: The results may vary depending on the hardware and environment in which the benchmarks are run. Ensure that the conditions are consistent with those used during benchmarking for accurate results.
