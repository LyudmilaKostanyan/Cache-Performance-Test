# Cache Hierarchy Performance Exploration

## Project Overview

This project aims to measure and analyze the performance of a system's cache hierarchy (L1, L2, L3) by accessing an array with increasing stride sizes. The program tests how different stride sizes affect memory access times, which can provide insights into the locality of memory and the impact on cache efficiency.

### Key Concepts:
- **Cache Hierarchy**: Modern processors typically have multiple cache levels, such as L1, L2, and L3 caches, to improve performance by storing frequently accessed data closer to the processor.
- **Stride Size**: This refers to the interval between successive memory accesses. Small strides (e.g., step 1) have better locality, while larger strides (e.g., step 256) tend to access memory locations that are farther apart, potentially causing cache misses and reducing performance.
- **Locality of Reference**: The principle that programs tend to access a small set of memory locations frequently, which is key for optimizing cache performance.

The program measures the average access times for different stride sizes and provides insight into how varying stride lengths interact with the cache system.

## Example Output

```
Cache Performance Test
---------------------------------
    Stride |  Avg Time (ns)
---------------------------------
         1 |        14073.00 ns
        16 |        14142.00 ns
        64 |        14722.00 ns
       256 |        15446.00 ns
      1024 |        38753.00 ns
      4096 |        64826.00 ns
```

## Explanation of Output

The program outputs the following information:
- **Stride**: The memory access stride size in bytes (e.g., 1, 16, 64, etc.).
- **Avg Time (ns)**: The average time, in nanoseconds, taken for accessing memory with the given stride size. This time is measured over multiple iterations (specified by `ITERATIONS`) to get an accurate measurement.

### Interpretation of the output:
- **Small Strides (1, 16, 64)**: Typically result in lower access times, as they exhibit better cache locality and tend to stay within the cache's working set (e.g., L1 cache).
- **Large Strides (1024, 4096)**: Lead to higher access times because they cause more cache misses and may result in fetching data from slower cache levels (e.g., L2 or L3 caches), or even main memory.

By comparing the average times, you can observe how increasing stride size impacts performance due to cache misses and locality.

## Build and Run

### Instructions:

1. **Clone the repository:**
   If you haven't cloned the repository yet, do so by running:
   ```bash
   git clone https://github.com/LyudmilaKostanyan/Cache-Performance-Test.git
   cd Cache-Performance-Test
   ```

2. **Build the project:**
   Once you're in the project directory, compile the code with:
   ```bash
   cmake -S . -B build
   cmake --build build
   ```

3. **Run the compiled executable:**
   After compiling, you can run the program:
   ```bash
   cd build
   ./main
   ```
