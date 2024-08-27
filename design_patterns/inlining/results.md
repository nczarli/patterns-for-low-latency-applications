# Inlining Benchmark Results

This document summarizes the results of benchmarking the performance impact of function inlining in a C++ program.

## What is Inlining?

Inlining is an optimization technique used by compilers where the compiler replaces a function call with the actual code of the function. This eliminates the overhead associated with calling a function, such as saving the return address, passing arguments, and jumping to the function code.

### Key Characteristics of Inlining:
- **Reduced Function Call Overhead**: Since the function code is directly inserted where the function is called, there's no overhead from the function call.
- **Potential for Further Optimizations**: The compiler can apply additional optimizations to the inlined code that wouldn't be possible with a regular function call.
- **Code Size Trade-off**: Inlining can increase the size of the binary because the function code is duplicated wherever the function is called.

Inlining is particularly useful in performance-critical sections of code where small functions are called frequently.

## Benchmark Overview

The benchmark compares two scenarios:

- **Without Inlining** (`BM_WithoutInline`): A function call is made without inlining.
- **With Inlining** (`BM_WithInline`): The function is inlined by the compiler.

### Results

| Benchmark           | Time (ns) | CPU Time (ns) | Iterations   |
|---------------------|-----------|---------------|--------------|
| **BM_WithoutInline** | 1.13      | 1.13          | 614,147,811  |
| **BM_WithInline**    | 0.842     | 0.842         | 835,221,271  |

### Interpretation

- **Without Inlining**:
  - Each function call took approximately **1.13 nanoseconds**.
  - The number of iterations achieved was lower compared to the inlined version.

- **With Inlining**:
  - The function call, when inlined, took approximately **0.842 nanoseconds**.
  - The benchmark with inlining performed significantly more iterations, indicating a higher efficiency.

### Conclusion

The results demonstrate that inlining provides a noticeable performance improvement by reducing the time taken per function call. In performance-critical sections, enabling inlining can lead to a more efficient execution, particularly for small, frequently called functions.

## Running the Benchmark

To reproduce these results, navigate to the `inlining` directory and follow these steps:

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

**Note**: The results may vary depending on the hardware and environment in which the benchmarks are run.
