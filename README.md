# Matrix-Free PDE Performance Study

This project explores how different implementations can affect the runtime and memory usage of numerical PDE computations.

I started with a simple 2D heat equation and then looked at two performance questions:

1. How does loop ordering affect runtime?
2. How does a matrix-free Laplacian compare with a sparse CSR matrix?

## What I Did
- Implemented a 2D heat equation using finite differences.
- Compared two Numba stencil loops with different loop orderings.
- Compared a sparse CSR Laplacian with a matrix-free stencil implementation.
- Checked that the different implementations produced the same numerical result.
- Measured runtime and estimated memory usage for different grid sizes.

## Main Results
- On a 2048 x 2048 grid, changing the loop ordering produced about an ~8x runtime difference in one benchmark.
- On a 1024 x 1024 grid, the matrix-free Laplacian was about ~3.5x faster than the CSR implementation in the recorded benchmark.
- At 2.36 million degrees of freedom, the matrix-free approach used about 5x less estimated working memory because the sparse matrix did not need to be stored explicitly.

The exact numbers depend on the computer and implementation, so the main goal of this project is to understand why these performance differences can occur.

## Notebooks
- 01_2D-Heat-Eq.ipynb — 2D heat equation using finite differences
- 02_memory_locality.ipynb — effect of loop ordering and memory access
- 03_matrix_free_laplacian.ipynb — CSR versus matrix-free Laplacian

## Key Takeaways
This project helped me see that numerical performance depends on more than the mathematical algorithm. Memory access, data storage, and implementation choices can have a large effect on runtime and memory usage, especially as problems become larger.

## Tools
Python, NumPy, SciPy, Numba, and Matplotlib

## Future Work
Extend this project by implementing the same operators in C++ and exploring parallel programming with OpenMP and MPI.
