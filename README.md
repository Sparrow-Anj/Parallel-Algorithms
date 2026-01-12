#  Parallel Algorithms — Parallel Matrix Multiplication

This repository contains my implementation of **Sequential** and **Parallel Matrix Multiplication** in C++.  
I built this while learning **concurrency, multithreading, and parallel execution**, and this project helped me understand how computation can be distributed across CPU cores to achieve real speedup.

---

##  Overview

This repository includes:

- **Sequential Matrix Multiplication**  
  A standard three-loop implementation.

- **Parallel Matrix Multiplication**  
  Rows of the result matrix are divided among multiple threads, allowing computation to run simultaneously.

Matrix multiplication is an ideal problem for parallelism because each row of the output can be computed independently.

---

##  How Parallelization Works

For a result matrix `C`:

C[i][j] = Σ (A[i][k] * B[k][j])


Each row of `C` can be computed separately.  
Parallel version assigns different row blocks to different threads:

Thread 1 → rows 0 to n/p
Thread 2 → rows n/p to 2n/p
...
Thread p → rows (p-1)n/p to n


This reduces total computation time on multi-core systems.

---

##  Repository Structure

Parallel-Algorithms/
└── Parallel Matrix Multiply.cpp # Contains both Sequential + Parallel implementations


---

## How to Compile & Run

### **Compile (Sequential + Parallel code together)**

```bash
g++ -std=c++17 -pthread Parallel\ Matrix\ Multiply.cpp -o matrix

./matrix

## Performance Notes

You typically see meaningful speedup for large matrices:
Matrix size ≥ 500×500
Threads used ≈ number of CPU cores
Smaller matrices may not show improvement because thread creation overhead becomes dominant.



