# Loop Unrolling Benchmark Results

This document summarizes the results of benchmarking the performance impact of loop unrolling in C++.

## What is Loop Unrolling?

Loop unrolling is a performance optimization technique used to improve the execution speed of loops by reducing the overhead of loop control operations. This technique involves expanding the loop body multiple times, thus decreasing the number of iterations and control instructions.

### Key Characteristics of Loop Unrolling:
- **Reduced Loop Overhead**: By increasing the size of the loop body, the number of iterations is reduced, leading to fewer loop control instructions and less overhead.
- **Increased Instruction-Level Parallelism**: Unrolled loops can exploit the CPU’s capability to execute multiple instructions in parallel.
- **Increased Code Size**: Unrolling loops increases the size of the binary because the loop body is duplicated.

Loop unrolling is particularly effective in scenarios where loops are executed many times and the cost of loop control is significant compared to the cost of the loop body operations.

## Benchmark Overview

The benchmark compares two scenarios:

- **Loop Without Unrolling** (`BM_LoopWithoutUnrolling/1000`): A loop executed without unrolling.
- **Loop With Unrolling** (`BM_LoopWithUnrolling/1000`): A loop executed with unrolling.

### Results

| Benchmark                        | Time (ns) | CPU Time (ns) | Iterations |
|----------------------------------|-----------|---------------|------------|
| **BM_LoopWithoutUnrolling/1000**  | 1,829     | 1,829         | 377,713    |
| **BM_LoopWithUnrolling/1000**     | 568       | 568           | 1,189,037  |

### Interpretation

- **Loop Without Unrolling**:
  - Each iteration took approximately **1,829 nanoseconds**.
  - The total number of iterations achieved was lower compared to the unrolled loop.

- **Loop With Unrolling**:
  - Each iteration took approximately **568 nanoseconds**.
  - The unrolled loop demonstrated a significant reduction in execution time, resulting in a higher number of iterations.

### Conclusion

The results illustrate that loop unrolling provides a substantial performance improvement by reducing loop overhead and increasing the number of iterations. This optimization technique can significantly enhance the performance of loops, especially in cases where the loop body contains computationally intensive operations.

## Running the Benchmark

To reproduce these results, navigate to the `loop_unrolling` directory and follow these steps:

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
