# Compile-Time vs. Runtime Dispatch Benchmark Results

This document summarizes the results of benchmarking the performance of compile-time dispatch versus runtime dispatch in C++.

## What is Compile-Time Dispatch?

**Compile-time dispatch** is a technique used to resolve method calls or function dispatching at compile time rather than at runtime. This method leverages templates and template specialization to determine the method to call during the compilation phase, resulting in more efficient code with reduced overhead during execution.

### Key Characteristics:
- **Efficiency**: Compile-time dispatch avoids the overhead associated with runtime polymorphism by resolving function calls at compile time.
- **Performance**: Generally results in faster execution as there is no need for virtual table lookups or dynamic type checks at runtime.
- **Use Cases**: Ideal for performance-critical applications where reducing runtime overhead is essential, such as high-performance computing and real-time systems.

## Benchmark Overview

The benchmark compares two dispatch mechanisms:

- **Runtime Dispatch** (`BM_RuntimeDispatch`): Uses virtual functions to determine method calls at runtime.
- **Compile-Time Dispatch** (`BM_CompileTimeDispatch`): Uses template-based dispatch to resolve method calls at compile time.

### Results

| Benchmark                       | Time (ns) | CPU Time (ns) | Iterations |
|---------------------------------|-----------|---------------|------------|
| **BM_RuntimeDispatch/1**        | 1.24      | 1.24          | 563,320,273|
| **BM_RuntimeDispatch/2**        | 1.19      | 1.19          | 585,140,902|
| **BM_CompileTimeDispatch<Derived1>** | 1.01   | 1.01          | 681,408,233|
| **BM_CompileTimeDispatch<Derived2>** | 1.01   | 1.01          | 686,642,766|

### Interpretation

- **Runtime Dispatch**:
  - **BM_RuntimeDispatch/1**: Each operation took approximately **1.24 nanoseconds**.
  - **BM_RuntimeDispatch/2**: Each operation took approximately **1.19 nanoseconds**.
  - Performance is slightly variable depending on the derived class used.

- **Compile-Time Dispatch**:
  - **BM_CompileTimeDispatch<Derived1>**: Each operation took approximately **1.01 nanoseconds**.
  - **BM_CompileTimeDispatch<Derived2>**: Each operation took approximately **1.01 nanoseconds**.
  - Both derived classes show consistent performance, significantly faster compared to runtime dispatch.

### Conclusion

The results show that compile-time dispatch is generally more efficient than runtime dispatch. The compile-time dispatch method provides faster execution times, as it avoids the overhead of virtual function calls and dynamic dispatch. This makes compile-time dispatch preferable for scenarios where performance is critical.

## Running the Benchmark

To reproduce these results, navigate to the `compile-time_dispatch` directory and follow these steps:

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
