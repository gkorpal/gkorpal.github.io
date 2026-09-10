---
title: "Surrounded by transforms"
date: 2026-09-10
permalink: /posts/2026/09/transforms/
tags:
  - fourier
  - harmonic-analysis
  - group-theory
  - quantum-computing
  - laplace
  - mellin
  - integral-transforms
---

An [integral transform](https://en.wikipedia.org/wiki/Integral_transform), or discrete transform, is a **change of basis**: an operation that re-expresses a function or signal defined on a "spatial" or "time" domain in terms of a different set of basis functions.

The purpose of such a transform is typically to **diagonalize a linear operator**. Operations that are difficult to work with in the original domain — differentiation, scaling, cyclic shifting, convolution — become pointwise multiplication in the transform domain. For a kernel $K(t, u)$, the transform $\mathcal{T}$ of a function $f$ is defined as

$$(\mathcal{T}f)(u) = \int_{t_1}^{t_2} f(t) K(t, u) \, dt$$

In the discrete case, the integral is replaced by a summation and the kernel by a transformation matrix.


## Criteria for "Fourier-Type" Transforms

A transform belongs to the [Fourier-related family](https://en.wikipedia.org/wiki/List_of_Fourier-related_transforms) if it is rooted in **Abstract Harmonic Analysis** — that is, if it acts as a projection onto the character space of an underlying group.

Four algebraic properties define membership in this family:
1. **Group Domain ($G$):** The input space forms a topological group under a symmetry operation (e.g., addition in $\mathbb{R}$, multiplication in $\mathbb{R}^+$, or modular arithmetic in $\mathbb{Z}_N$).
2. **Dual Group of Characters ($\hat{G}$):** The kernels are group *characters* — homomorphisms mapping the group operation to multiplication on the complex unit circle.
3. **The Convolution Theorem:** Group convolution $f * g$ maps to pointwise multiplication: $\mathcal{F}(f * g) = \mathcal{F}(f) \cdot \mathcal{F}(g)$.
4. **Plancherel Isometry:** The transform preserves inner products and energy (the $L^2$ norm) between the spatial and frequency domains.

Properties 2 and 3 are stated here for the **abelian** case, which covers most entries below. For **non-abelian groups** (e.g. $S_n$, $SO(3)$, $SU(2)$), both properties generalize rather than fail: characters are replaced by the matrix coefficients of irreducible unitary representations, and the convolution theorem becomes pointwise *matrix* multiplication at each irrep rather than scalar multiplication. This is the form under which the Finite Non-Abelian Fourier and Peter-Weyl transforms remain part of the same family.


## Timeline of Development and Family Tree

The table below indexes major continuous, discrete, geometric, and non-abelian transforms in chronological order of development.

| Year | Transform | Classification Type | Domain / Group ($G$) | Operator Diagonalized | Primary Application / Field |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1782** | **[Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform)** | Continuous | Non-negative reals $([0, \infty), +)$ | Differentiation operator $\frac{d}{dt}$ | Control theory, ODE stability, circuit analysis |
| **1782** | **[Spherical Harmonic Transform](https://en.wikipedia.org/wiki/Spherical_harmonics)** | Geometric / Spatial | 2-Sphere $S^2$ / $SO(3)$ | Angular Laplacian $\nabla_{S^2}^2$ | Planetary gravity, quantum orbitals, 3D graphics |
| **1805** | **[Discrete Fourier Transform (DFT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)** | Discrete / Finite | Cyclic group $(\mathbb{Z}_N, +)$ | Cyclic shift matrix | Asteroid orbit interpolation, digital signal processing |
| **1807** | **[Continuous Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)** | Continuous | Real line $(\mathbb{R}, +)$ | Differentiation operator $\frac{d}{dt}$ | Wave mechanics, heat diffusion, quantum physics |
| **1869** | **[Hankel Transform](https://en.wikipedia.org/wiki/Hankel_transform)** | Geometric / Radial | Radial Euclidean space $(\mathbb{R}^n)$ | Radial Laplacian $\nabla_r^2$ | Cylindrical wave acoustics, optics, fluid dynamics |
| **1893** | **[Hadamard Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | Discrete / Combinatorial | Sign matrix group $\{+1,-1\}^{N \times N}$ | Recursive orthogonal sign-flip basis (Sylvester construction) | Error-correcting codes, orthogonal design theory |
| **1896** | **[Fourier Transform on Finite Groups](https://en.wikipedia.org/wiki/Fourier_transform_on_finite_groups)** | Non-Abelian / Discrete | Finite groups ($S_n, D_n, GL_2(\mathbb{F}_q)$) | Left regular representation | Finite group representation theory, Diaconis card shuffling |
| **1896** | **[Mellin Transform](https://en.wikipedia.org/wiki/Mellin_transform)** | Continuous / Multiplicative | Multiplicative reals $(\mathbb{R}^+, \times)$ | Dilation operator $x \frac{d}{dx}$ | Analytic number theory, Dirichlet series, Riemann $\zeta$ |
| **1917** | **[Radon Transform](https://en.wikipedia.org/wiki/Radon_transform)** | Geometric / Spatial | Hyperplane lines in $\mathbb{R}^n$ | Integral projection geometry | CT / PET medical tomography, seismic imaging |
| **1923** | **[Walsh Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | Discrete / Quantum-adjacent | Hypercube $(\mathbb{Z}_2)^n$ | Bitwise XOR shift | Spread-spectrum coding, Simon's quantum algorithm |
| **1927** | **[Peter-Weyl Transform](https://en.wikipedia.org/wiki/Peter%E2%80%93Weyl_theorem)** | Non-Abelian / Continuous | Compact Lie groups ($SO(3), SU(2)$) | Lie algebra differential operators | Quantum angular momentum, particle physics |
| **1942** | **[Hartley Transform](https://en.wikipedia.org/wiki/Hartley_transform)** | Continuous / Real-Valued | Real line $(\mathbb{R}, +)$ | Shift operator on real fields | Real-valued signal processing without complex arithmetic |
| **1947** | **[Z-Transform](https://en.wikipedia.org/wiki/Z-transform)** | Discrete-Time | Discrete grid $\mathbb{Z}$ | Discrete linear time-shift | Digital filter design (IIR/FIR), sampled data control |
| **1965** | **[Fast Fourier Transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform)** | Fast Algorithm | Cyclic group $(\mathbb{Z}_N, +)$ | Fast $O(N \log N)$ matrix factorization | Modern digital telecom, spectral analysis, fast convolution |
| **1969** | **[Chirp Z-Transform (CZT)](https://en.wikipedia.org/wiki/Chirp_Z-transform)** | Discrete / Complex | Spiral contours in $\mathbb{C}$ | Non-uniform Z-plane evaluation | Zoomed spectrum analysis, radar signal processing |
| **1971** | **[Number-Theoretic Transform (NTT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_(general)#Number-theoretic_transform)** | Finite Field / Discrete | Galois fields $\mathbb{F}_q^\times$ | Modular polynomial shift | Exact integer convolution, post-quantum cryptography |
| **1980** | **[Fractional Fourier Transform (FrFT)](https://en.wikipedia.org/wiki/Fractional_Fourier_transform)** | Continuous / Phase Space | Time-frequency plane | Quantum Harmonic Oscillator | Chirped optical signals, radar filtering |
| **1994** | **[Quantum Fourier Transform (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform)** | Discrete / Quantum | Cyclic group $(\mathbb{Z}_{2^n}, +)$ | Quantum phase shift gates | Shor's factoring algorithm, quantum computation |
| **1998** | **[Higher-Order Fourier Analysis](https://en.wikipedia.org/wiki/Gowers_norm)** | Non-Linear / Combinatorial | Integers / Finite fields | Gowers Uniformity Norms ($e^{2\pi i P(n)}$) | Additive combinatorics, Green-Tao prime theorem |
