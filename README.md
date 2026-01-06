````markdown
# Mandelbrot OpenMP

Compute the Mandelbrot set using Fortran and OpenMP, demonstrating parallel performance scaling on multi-core CPUs.

---

## Table of Contents

- [Purpose](#purpose)
- [Requirements](#requirements)
- [Compilation](#compilation)
- [Running the Program](#running-the-program)
- [Output](#output)
- [Performance and Scaling](#performance-and-scaling)
- [Repository Structure](#repository-structure)
- [License](#license)

---

## Purpose

This project demonstrates:

- **Parallel computation** of the Mandelbrot set using Fortran and OpenMP.
- **CPU scaling analysis** by adjusting the number of threads (`OMP_NUM_THREADS`) and measuring wall time.
- **Best practices** for OpenMP: computing in parallel, then writing output serially to avoid thread contention.

This is a small, reproducible example suitable for learning **scientific computing, parallel programming, and performance optimization**.

---

## Requirements

- Linux or Unix-like environment (tested on Kali Linux in VMware)
- `gfortran` compiler with OpenMP support
- Terminal access

Optional: `nano` or `vim` to edit the source code

---

## Compilation

Use the following command to compile the Fortran program:

```bash
gfortran -O3 -fopenmp -o mandf mandf.f90
````

* `-O3` → enables high optimization
* `-fopenmp` → enables OpenMP parallelization
* `-o mandf` → sets the output executable name

---

## Running the Program

Set the number of threads using the `OMP_NUM_THREADS` environment variable:

```bash
export OMP_NUM_THREADS=4   # Use 4 threads (matches your physical cores)
./mandf > mand.dat
```

* `mand.dat` will contain the computed iteration counts for the Mandelbrot set.
* Timing information is printed to the terminal:

```
clock time : X.XXXs  wall time= Y.YYYs
```

* **Wall time** is the actual elapsed time and shows the effect of parallel scaling.

---

## Output

* `mand.dat` → contains the Mandelbrot iteration counts in a 2D grid.
* Optional: visualize the Mandelbrot set using Python, MATLAB, or Gnuplot.

Example snippet from `mand.dat`:

```
1.0000000000000000 0.995996 0.500000
1.0000000000000000 0.997998 0.500000
...
```

---

## Performance and Scaling

* Tested on an **Intel i7-8550U (4 cores, 8 threads)**
* Wall time decreases as `OMP_NUM_THREADS` increases, but **best efficiency occurs when using ≤ physical cores**
* Hyperthreading helps slightly beyond physical cores, but diminishing returns occur for too many threads.

Example wall times:

| Threads | Wall time (s) |
| ------- | ------------- |
| 1       | 2.076         |
| 2       | 1.575         |
| 3       | 1.482         |
| 4       | 1.594         |
| 8       | 0.910         |

---

## Repository Structure

```
mandelbrot-openmp/
├── mandf.f90          # Fortran source code (OpenMP parallel Mandelbrot)
├── README.md          # This file
├── mandc.cc           # Optional C++ version
├── mand.dat           # Optional small example output
└── plot.png           # Optional scaling plot
```

---

## License

This project is licensed under the **MIT License**. You are free to use, modify, and distribute this code with attribution.

---



```

