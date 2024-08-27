# Constexpr Benchmark Results

This document summarizes the results of benchmarking the performance impact of using `constexpr` in C++.

## What is `constexpr`?

In C++, `constexpr` is a keyword used to indicate that a function or variable can be evaluated at compile time. When a function is declared as `constexpr`, it means that the function's return value can be computed at compile time if all its inputs are known at compile time. This can lead to performance improvements by avoiding runtime computations.

### Key Characteristics of `constexpr`:
- **Compile-Time Evaluation**: Functions and variables marked as `constexpr` are evaluated during compilation, reducing runtime overhead.
- **Improved Performance**: By evaluating expressions at compile time, the program can be more efficient at runtime.
- **Increased Type Safety**: Ensures that certain expressions are evaluated in a controlled manner, which can help catch errors at compile time.

Using `constexpr` can be particularly beneficial in cases where the values of computations are known ahead of time and can be precomputed to improve performance.

## Benchmark Overview

The benchmark compares two scenarios:

- **Constexpr Factorial** (`BM_ConstexprFactorial`): A factorial function evaluated at compile time using `constexpr`.
- **Runtime Factorial** (`BM_RuntimeFactorial`): A factorial function evaluated at runtime.

### Results

| Benchmark               | Time (ns) | CPU Time (ns) | Iterations   |
|-------------------------|-----------|---------------|--------------|
| **BM_ConstexprFactorial** | 30.7      | 30.7          | 22,730,462   |
| **BM_RuntimeFactorial**   | 36.1      | 36.1          | 19,679,087   |

### Interpretation

- **Constexpr Factorial**:
  - Each computation took approximately **30.7 nanoseconds**.
  - The `constexpr` evaluation resulted in a higher number of iterations, indicating a more efficient computation.

- **Runtime Factorial**:
  - Each computation took approximately **36.1 nanoseconds**.
  - The runtime evaluation was slower compared to the `constexpr` evaluation.

### Conclusion

The results show that using `constexpr` for compile-time evaluations provides a performance advantage over runtime computations. By moving computations to compile time, programs can run more efficiently, with faster execution times and higher iteration counts.

## Running the Benchmark

To reproduce these results, navigate to the `constexpr` directory and follow these steps:

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
 