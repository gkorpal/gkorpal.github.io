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
  - linear-algebra
  - spectral-theory
---

An [integral transform](https://en.wikipedia.org/wiki/Integral_transform) (resp. discrete transform) $\mathcal{T}$ is a **change of basis**: it re-expresses a function (resp. sequence) $f$ on one domain $D$ in terms of a different set of basis functions. For a kernel $K(t, u)$,

$$(\mathcal{T}f)(u) = \int_{D} f(t)  K(t, u)   dt \quad \Big(\text{resp.} \sum_{t \in D} f(t)  K(t, u)\Big)$$

where $D$ can be an interval, a ring of $N$ points, the positive reals under multiplication, the surface of a sphere. What every such domain carries is a symmetry, an operation under which it looks the same from any of its points. That symmetry is a **group** $G$, and the third column below names it for each transform.

From Laplace in the 1780s to wavelets in the 1980s, the whole zoo is one idea repeated, and the idea is a piece of linear algebra from a first course. Here it is in one sentence, and the rest of the post is a map of how far it reaches.

> A transform is the change of basis that makes the symmetry of its domain act diagonally; the variety of transforms is the variety of domains and their symmetries, and the thread frays in one predictable order as the symmetry becomes less commutative: abelian group, then a Gelfand pair, then a non-abelian group, then an equivariant map, where no diagonal is left at all.

The table is in the order of history. The sections after it are in the order of the sentence, one stage each, and the last column of the table says which stage each transform belongs to. Everything else in the zoo is a child of one of these twelve, and each stage ends with a table of the children of its rows, in the same columns without the year, with the parent named in place of the stage.

## The transforms in chronological order

| Year | Transform | Domain / symmetry ($G$) | Kernel | Primary application | Stage |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1754** | **[Discrete Fourier Transform (DFT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)** | [Cyclic group](https://en.wikipedia.org/wiki/Cyclic_group) $(\mathbb Z_N, +)$ | $e^{-2\pi i jk/N}$ | Orbit determination, and thereafter the whole of digital signal processing[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1782** | **[Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform)** | $(\mathbb{R}, +)$ on functions supported in $[0,\infty)$, the character $e^{-st}$ continued to $\Re s > 0$ | $e^{-st}$ | Control theory, ODE stability, circuit analysis[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1782** | **[Spherical Harmonic Transform](https://en.wikipedia.org/wiki/Spherical_harmonics)** | 2-sphere $S^2 = SO(3)/SO(2)$, the [rotation group](https://en.wikipedia.org/wiki/3D_rotation_group) modulo rotations about an axis | $\overline{Y_\ell^m(\theta,\varphi)}$ | Geopotential models, atomic orbitals, CMB analysis[^legendre] | [Gelfand pair (2)](#stage-two-gelfand-pairs) |
| **1807** | **[Fourier Series](https://en.wikipedia.org/wiki/Fourier_series)** | [Circle group](https://en.wikipedia.org/wiki/Circle_group) $\mathbb{T} = \mathbb{R}/2\pi\mathbb{Z}$ | $e^{-in\theta}$ | Heat conduction in a bar, vibrating strings, every periodic signal[^series] | [abelian (1)](#stage-one-abelian-groups) |
| **1822** | **[Continuous Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)** | Real line $(\mathbb{R}, +)$ | $e^{-i\omega t}$ | Heat conduction, wave mechanics, quantum theory[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1875** | **[Hankel Transform](https://en.wikipedia.org/wiki/Hankel_transform)** | $SO(n)$-invariant functions on $\mathbb{R}^n$: the motion group of $\mathbb{R}^n$ modulo its rotations, a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) | $t J_\nu(ut)$ | Axisymmetric boundary value problems, optics, acoustics[^hankel] | [Gelfand pair (2)](#stage-two-gelfand-pairs) |
| **1896** | **[Mellin Transform](https://en.wikipedia.org/wiki/Mellin_transform)** | Multiplicative reals $(\mathbb{R}^+, \times)$ | $t^{s-1}$ | Analytic number theory, Dirichlet series, asymptotics[^mellin] | [abelian (1)](#stage-one-abelian-groups) |
| **1897** | **[Fourier Transform on Finite Groups](https://en.wikipedia.org/wiki/Fourier_transform_on_finite_groups)** | Finite groups: [$S_n$](https://en.wikipedia.org/wiki/Symmetric_group), [$D_n$](https://en.wikipedia.org/wiki/Dihedral_group), [$GL_2(\mathbb F_q)$](https://en.wikipedia.org/wiki/General_linear_group) | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Representation theory, card shuffling, spectral graph theory[^frobenius] | [non-abelian (3)](#stage-three-non-abelian-groups) |
| **1917** | **[Radon Transform](https://en.wikipedia.org/wiki/Radon_transform)** | Lines in $\mathbb{R}^2$, affine hyperplanes in $\mathbb{R}^n$ | $\delta(u - \langle x, \theta \rangle)$ | CT and PET tomography, seismic imaging[^radon] | [equivariant (4)](#stage-four-equivariant-maps-symmetry-without-a-diagonal) |
| **1927** | **[Peter-Weyl Transform](https://en.wikipedia.org/wiki/Peter%E2%80%93Weyl_theorem)** | [Compact Lie groups](https://en.wikipedia.org/wiki/Compact_group) $SO(3)$, [$SU(2)$](https://en.wikipedia.org/wiki/Special_unitary_group) | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Angular momentum, particle physics, molecular replacement[^frobenius] | [non-abelian (3)](#stage-three-non-abelian-groups) |
| **1946** | **[Gabor Transform / STFT](https://en.wikipedia.org/wiki/Short-time_Fourier_transform)** | Time-frequency plane, the [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) | $\overline{g(t-b)} e^{-i\omega t}$ | Spectrograms, speech, time-frequency analysis[^wavelet] | [equivariant (4)](#stage-four-equivariant-maps-symmetry-without-a-diagonal) |
| **1984** | **[Wavelet Transform](https://en.wikipedia.org/wiki/Continuous_wavelet_transform)** | The [affine](https://en.wikipedia.org/wiki/Affine_group), or "$ax+b$", group | $a^{-1/2} \overline{\psi((t-b)/a)}$ | JPEG 2000, denoising, LIGO analysis[^wavelet] | [equivariant (4)](#stage-four-equivariant-maps-symmetry-without-a-diagonal) |

Twelve transforms, two and a half centuries, a dozen fields. Each row is a different domain with a different symmetry; the last column is the thread.

## What a transform does

The idea is [diagonalization](https://en.wikipedia.org/wiki/Diagonalizable_matrix). A unitary change of basis, $A \mapsto U A U^{\ast}$, brings every [normal](https://en.wikipedia.org/wiki/Normal_matrix) operator to diagonal form; that is the [spectral theorem](https://en.wikipedia.org/wiki/Spectral_theorem), and it is the whole post in one line.[^halmos]

> An integral transform **is** the $U$.

Literally. Let $\tau_a$ be translation by $a$ on the real line and $\mathcal{F}$ the Fourier transform. Then

$$\mathcal{F} \tau_a \mathcal{F}^{-1} = \text{multiplication by } e^{-i a \xi}$$

A multiplication operator rescales its input point by point, as a diagonal matrix rescales each coordinate. So the Fourier transform is the $U$ that makes translation diagonal, and with it everything that commutes with translation, since [commuting normal operators](https://en.wikipedia.org/wiki/Commuting_matrices) share an eigenbasis: differentiation becomes multiplication by $i\xi$, and every [convolution](https://en.wikipedia.org/wiki/Convolution), every filter, becomes multiplication by the transform of its kernel.[^halmos] That is what the transform is for. A differential equation with constant coefficients becomes algebraic, and its solution comes back as a convolution of the data with a fixed kernel; the Coulomb potential and the heat kernel are the two classical cases, both found before the transform that explains them.[^mackey]

One caveat. Translation on $\mathbb{R}$ has no eigenvectors in $L^2$, since $e^{i\xi t}$ is not square-integrable, so there the "diagonal" is the [multiplication-operator form](https://en.wikipedia.org/wiki/Spectral_theorem#Multiplication_operator_version) of the spectral theorem. On a finite group of order $N$ the transform is an $N \times N$ unitary matrix and the first course applies verbatim; the finite case is the one this post leans on.

## Stage one: abelian groups

> A transform diagonalizes exactly those operators which **commute with the symmetry of the domain**.

If the domain carries a group action, the operators commuting with it are the convolution operators, and when $G$ is abelian they commute with each other, so they share one eigenbasis. That eigenbasis is the set of [characters](https://en.wikipedia.org/wiki/Character_group) of $G$, the functions with $\chi(xy) = \chi(x)\chi(y)$: convolving a character with anything returns a multiple of the same character, the multiple being the Fourier coefficient. So the group decides the kernel $K(t,u)$ of the table, which is just the characters written out; nothing is chosen. For a [locally compact abelian group](https://en.wikipedia.org/wiki/Locally_compact_abelian_group) this is [Pontryagin duality](https://en.wikipedia.org/wiki/Pontryagin_duality): the characters form the dual group $\hat G$, the transform turns convolution into multiplication and is an isometry ([Plancherel](https://en.wikipedia.org/wiki/Plancherel_theorem)), and in the language of Banach algebras it is the [Gelfand transform](https://en.wikipedia.org/wiki/Gelfand_representation) of $L^1(G)$.[^rudin]

This is the intact case, and it is five rows of the table on four groups.

- The **DFT** on $\mathbb Z_N$, the **Fourier series** on $\mathbb{T}$ and the **Fourier transform** on $\mathbb{R}$ are the same construction on the three classical groups, and the fourth, $\mathbb{Z}$, is the dual of $\mathbb{T}$: its Fourier transform is the Fourier series read backwards, and off the unit circle it is the Z-transform.[^series]
- The **Mellin transform** is the Fourier transform on $(\mathbb{R}^+, \times)$: substitute $x = e^{\xi}$.[^mellin]
- The **Laplace transform** is the Fourier transform on the half-line with the character continued off the unitary axis: $e^{-st}$ with $\Re s > 0$ is $e^{-i\omega t}$ at a complex frequency, which is why it decays. That makes the transform easier to handle, since the kernel decays and the result is analytic in $s$, and it costs orthogonality: the kernels $e^{-st}$ for real $s$ are not orthogonal, so there is no Plancherel formula on the real axis of $s$, and the isometry is recovered only line by line, on $\Re s = c$, where the Laplace transform of $f$ is the Fourier transform of $e^{-ct}f$.[^laplace]

The field variants of the DFT are settled by one more canonical form. The [Frobenius normal form](https://en.wikipedia.org/wiki/Frobenius_normal_form) decomposes a matrix over any field into [companion](https://en.wikipedia.org/wiki/Companion_matrix) blocks; the cyclic shift on $\mathbb Z_N$ is the companion matrix of $x^N - 1$, the [circulant matrices](https://en.wikipedia.org/wiki/Circulant_matrix) are $K[x]/(x^N-1)$, and the transform is decided by how $x^N - 1$ factors.

| Field $K$ | How $x^N - 1$ factors | Best canonical form | Transform |
| :--- | :--- | :--- | :--- |
| $\mathbb{C}$ | into $N$ distinct linear factors | Diagonal | **DFT** |
| $\mathbb{R}$ | into $x - 1$, also $x + 1$ when $N$ is even, and quadratics $x^2 - 2\cos(2\pi k/N) x + 1$ | $2 \times 2$ rotation blocks | **Hartley** |
| $\mathbb F_q$ | into distinct linear factors exactly when $N \mid q-1$ | Diagonal over $\mathbb F_q$ | **NTT** |

The middle row is the real spectral theorem: no real basis separates a conjugate pair of eigenvalues, so the Hartley kernel $\cos\nu x + \sin\nu x$ pairs $\nu$ with $-\nu$ and no real transform can do better.[^halmos] The last row says a change of field need cost nothing, provided $\mathbb F_q^\times$ contains an $N$th root of unity.

### Children of stage one

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **[Fast Fourier Transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform)** | $(\mathbb Z_N, +)$, the sum split along a subgroup of index two; any finite group with a chain of subgroups; Rader for prime $N$ | The DFT kernel, rearranged | Everything the DFT is used for, in $N \log N$ operations[^fft] | DFT |
| **[Walsh–Hadamard Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | $(\mathbb Z_2)^n$, the same construction on another finite abelian group | $(-1)^{\langle x, y \rangle}$ | Error-correcting codes, Mariner Mars telemetry, Simon's algorithm, the hidden subgroup problem on $(\mathbb Z_2)^n$[^hadamard] | DFT |
| **[Hartley Transform](https://en.wikipedia.org/wiki/Hartley_transform)** | $(\mathbb Z_N, +)$ or $(\mathbb{R}, +)$ over the real field, see the field table | $\cos ut + \sin ut$ | Signal processing without complex arithmetic | DFT |
| **[Number-Theoretic Transform (NTT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_(general)#Number-theoretic_transform)** | $(\mathbb Z_N, +)$ with $\omega$ a root of unity in $\mathbb F_q^\times$, see the field table | $\omega^{jk} \bmod q$ | Exact integer convolution, lattice cryptography | DFT |
| **[Discrete Cosine Transform (DCT)](https://en.wikipedia.org/wiki/Discrete_cosine_transform)** | $\mathbb Z_{2N}$ restricted to functions even under $n \mapsto -1-n$; the other reflections give the other fifteen cosine and sine transforms[^dct] | $\cos\frac{\pi k(2n+1)}{2N}$ | JPEG, MPEG, MP3 | DFT |
| **[Quantum Fourier Transform (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform)** | $(\mathbb Z_{2^n}, +)$ as a quantum circuit, the output read not as a spectrum but as a measurement of which irreducible representation the state lies in[^hsp] | $e^{2\pi i jk/2^n}$ | Shor's algorithm, the [hidden subgroup problem](https://en.wikipedia.org/wiki/Hidden_subgroup_problem) on $\mathbb{Z}$ | DFT |
| **[Generating Function](https://en.wikipedia.org/wiki/Generating_function)** | $(\mathbb{Z}, +)$, the characters $t^n$ continued off the unit circle, Laplace's original of 1782[^laplace] | $t^n$ | Difference equations, probability | Laplace |
| **[Z-Transform](https://en.wikipedia.org/wiki/Z-transform)** | $(\mathbb{Z}, +)$ continued off the unit circle; on it, the Fourier transform on $\mathbb{Z}$[^series] | $z^{-n}$ | Digital filter design, sampled-data control | Laplace |
| **[Chirp Z-Transform (CZT)](https://en.wikipedia.org/wiki/Chirp_Z-transform)** | Spiral contours in $\mathbb{C}$ | $A^{-n}W^{nk}$ | Zoom spectrum analysis, radar | Laplace |
| **Finite Laplace Transform** | $(0, T)$[^finite] | $e^{-st}$ | Problems on a finite time interval | Laplace |
| **[Finite Sine and Cosine Transforms](https://en.wikipedia.org/wiki/Fourier_sine_and_cosine_series)** | $[0, a]$, functions odd or even under reflection of the interval[^finite] | $\sin(n\pi x/a)$, $\cos(n\pi x/a)$ | Boundary value problems on an interval | Fourier series |
| **[Sine and Cosine Transforms](https://en.wikipedia.org/wiki/Sine_and_cosine_transforms)** | $[0, \infty)$, the transform restricted to odd and to even functions[^finite] | $\sin kx$, $\cos kx$ | Problems on a half-line | Fourier transform |
| **[Fractional Fourier Transform (FrFT)](https://en.wikipedia.org/wiki/Fractional_Fourier_transform)** | Phase-space rotations $SO(2)$: the power $\mathcal{F}^{2\alpha/\pi}$ on the [Hermite eigenbasis](https://en.wikipedia.org/wiki/Hermite_polynomials#Hermite_functions); the DFT has the same eigenvalues $\pm 1, \pm i$ but no canonical eigenbasis, so its fractional powers are a choice[^dftspectrum] | $e^{i\pi[(t^2+u^2)\cot\alpha - 2tu\csc\alpha]}$ | Chirped optical signals, radar | Fourier transform |
| **Hermite Transform** | $(\mathbb{R}, +)$, the expansion in the Hermite functions, the eigenbasis of $\mathcal{F}$ in which every fractional power is diagonal[^dftspectrum] | $e^{-x^2} H_n(x)$ | The quantum oscillator | Fourier transform |
| **[Laguerre Transform](https://en.wikipedia.org/wiki/Laguerre_polynomials)** | $[0, \infty)$; at parameters $\pm\tfrac12$ the Hermite expansion [split by parity](https://en.wikipedia.org/wiki/Hermite_polynomials#Relations_to_other_functions)[^polynomials] | $e^{-x} x^\alpha L_n^\alpha(x)$ | The hydrogen atom, the isotropic oscillator | Fourier transform |

## Stage two: Gelfand pairs

The **Hankel transform** acts on radial functions and the **spherical harmonic transform** on the sphere. Neither domain is a group: the sphere cannot be made one, and $SO(3)$, which acts on it, has no invariant one-dimensional space of functions but the constants.[^mackey] So there are no characters. Yet the transforms are diagonal: the Hankel transform turns the radial Laplacian into multiplication by $-\kappa^2$,[^hankel] and spherical harmonics are eigenfunctions of the Laplacian on the sphere.

What suffices is less than a commutative group. Write the domain as $X = G/K$, a group modulo the stabilizer $K$ of a point: $S^2 = SO(3)/SO(2)$, and $\mathbb{R}^n$ is the motion group of translations and rotations modulo the rotations $K = SO(n)$, so that the radial functions are the $K$-invariant functions on $G/K$. The operators on functions on $X$ that commute with $G$ form an algebra, and $(G, K)$ is a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) when that algebra is commutative; [symmetric spaces](https://en.wikipedia.org/wiki/Symmetric_space) are the motivating examples, and for radial functions the commutativity is elementary, since the operators commuting with the motion group are convolutions by radial kernels and the Fourier transform makes them multiplications by radial functions.[^hankel] When $(G, K)$ is a Gelfand pair, three things hold at once: the operators diagonalize simultaneously, as in the abelian case; the functions on $X$ split into pieces on which $G$ acts irreducibly, with no piece repeated; and each piece $V$ contains, up to scale, one function $u$ fixed by $K$. Writing $\rho(g)$ for the action of $g$ on $V$, the [spherical function](https://en.wikipedia.org/wiki/Zonal_spherical_function) of the piece is $\phi(g) = \langle u, \rho(g)u\rangle$, and it is an algebra homomorphism of the commutative algebra to $\mathbb{C}$ exactly as a character is for $L^1(G)$.[^gelfandpair] The spherical functions are the kernel, Legendre polynomials $P_\ell(\cos\theta)$ for $(SO(3), SO(2))$, Gegenbauer polynomials for $(SO(n), SO(n-1))$ and Bessel functions for the motion group, and the transform of $f$ is its inner products with the translates $\rho(g)u$. The Hankel transform is thus the Fourier transform on $\mathbb{R}^n$ restricted to the radial functions: for $f(x) = f_0(\lvert x \rvert)$ the transform is $F_0(r) = 2\pi r^{-(n-2)/2}\int_0^\infty f_0(s) J_{(n-2)/2}(2\pi r s) s^{n/2}\,ds$, a Hankel transform of order $(n-2)/2$. The other orders in the table come from the other pieces of $L^2(\mathbb{R}^n)$: on functions $f_0(\lvert x \rvert)P(x)$ with $P$ a harmonic polynomial of degree $k$, the Fourier transform is $P$ times a Hankel transform of order $k + (n-2)/2$.[^legendre]

The abelian case is not a separate theory. With $K = \{1\}$, $(G, \{1\})$ is a Gelfand pair if and only if $G$ is abelian.[^gelfandpair] The real hypothesis was never commutativity of $G$ but commutativity of the operators that commute with $G$, equivalently no repeated piece. This is the first place the transforms need representation theory, and for one job: to say when a transform is still diagonal.

### Children of stage two

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **[Legendre Transform](https://en.wikipedia.org/wiki/Legendre_polynomials)** | Zonal functions on $S^2$, those fixed by $SO(2)$: the spherical functions of $(SO(3), SO(2))$[^legendre] | $P_\ell(\cos\theta)$ | Axisymmetric potential problems | Spherical harmonic |
| **[Gegenbauer Transform](https://en.wikipedia.org/wiki/Gegenbauer_polynomials)** | Zonal functions on $S^{n-1}$: the spherical functions of $(SO(n), SO(n-1))$, with $\lambda = (n-2)/2$; $n = 3$ is Legendre[^gegenbauer] | $(1-x^2)^{\lambda - 1/2} P_k^\lambda(x)$ | Potential problems in $n$ dimensions | Spherical harmonic |
| **[Finite Hankel Transform](https://en.wikipedia.org/wiki/Fourier%E2%80%93Bessel_series)** | $0 < r < a$, the Fourier–Bessel series: compact domain, discrete spectrum[^finite] | $r J_n(r k_i)$ | Vibrating membranes, heat in a cylinder | Hankel |

## Stage three: non-abelian groups

The **Fourier transform on a finite group** and the **Peter–Weyl transform** act on functions on a non-commutative $G$, and now the convolution operators do not commute with each other, so no single eigenbasis exists. What replaces a character is an [irreducible representation](https://en.wikipedia.org/wiki/Irreducible_representation) $\pi$, a homomorphism from $G$ to unitary $d_\pi \times d_\pi$ matrices with no proper nonzero invariant subspace; a character is the case $d_\pi = 1$. The transform of $f$ at $\pi$ is the matrix $\hat f(\pi) = \sum_g f(g)\pi(g)$, and convolution becomes matrix multiplication, block by block. That this is a ring isomorphism $L(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$ is [Wedderburn's theorem](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem), the abelian case being the one where every block is $1 \times 1$.[^wedderburn] On its face this is a defeat: block-diagonal is not diagonal.

One observation rescues it. Let $G \times G$ act on functions on $G$ by translating on both sides, $f(g) \mapsto f(g_1^{-1} g g_2)$. Under that larger action the decomposition $L(G) = \bigoplus_\pi V_\pi \otimes V_\pi^{\ast}$ has no repeated piece, so $G \times G$ with its diagonal subgroup $\Delta G = \{(g, g)\}$ is a Gelfand pair, and its spherical functions are $\chi_\pi / d_\pi$, where $\chi_\pi(g) = \mathrm{tr} \pi(g)$ is what "character" means for a non-abelian group.[^wedderburn] So the non-abelian transform is a diagonalization after all, of the two-sided action; the $d_\pi \times d_\pi$ blocks are what the one-sided action alone can see. The history ran the same way: Frobenius invented representation theory in 1897 to answer a question of Dedekind's about group determinants, and it took until Weyl, thirty years later, for anyone to see that he had extended Fourier analysis from commutative to non-commutative groups.[^frobenius]

Two payoffs. A [Cayley graph](https://en.wikipedia.org/wiki/Cayley_graph) on $G$ has adjacency matrix equal to convolution by the indicator $\delta_S$ of its generating set $S$, so its eigenvalues are those of the blocks $\hat\delta_S(\pi)$, each repeated $d_\pi$ times; when $G$ is abelian, or $S$ is a union of conjugacy classes, the blocks are scalars and the eigenvalues are the character sums $\frac{1}{d_\pi}\sum_{s \in S} \chi_\pi(s)$ themselves.[^diaconis] And a shuffle is a probability $P$ on $S_n$, $k$ shuffles is $P^{\ast k}$, so $\widehat{P^{\ast k}} = \hat P^k$ and Plancherel bounds the [total-variation distance](https://en.wikipedia.org/wiki/Total_variation_distance_of_probability_measures) $\lVert P^{\ast k} - U \rVert = \max_A \lvert P^{\ast k}(A) - U(A) \rvert$ from the uniform distribution $U$ by a sum over representations:

$$\lVert P^{\ast k} - U \rVert^2 \le \frac14 \sum_{\pi \neq 1} d_\pi \mathrm{Tr}\big(\hat P(\pi)^k \hat P(\pi)^{\ast k}\big)$$

Put $\mathbb Z_p$ into it, stepping by $\pm 1$, and somewhat more than $p^2$ steps are needed; put $S_n$ in, swapping a random pair each step, and $\frac12 n\log n$ shuffles suffice, the distance staying near $1$ until then and collapsing after, which is the [cutoff phenomenon](https://en.wikipedia.org/wiki/Cutoff_phenomenon).[^diaconis]

This is also where the canonical forms of the first course meet the groups: classifying the elements of a matrix group up to conjugacy is the problem of canonical forms, and the four forms below are all the post ever uses.[^diaconis]

| Normal form | Canonical form of | Transform | Representation theory |
| :--- | :--- | :--- | :--- |
| **[Diagonal](https://en.wikipedia.org/wiki/Spectral_theorem)** | Normal matrices, unitary similarity | Stages one and two, the abelian groups and the Gelfand pairs | Every irreducible piece appears once |
| **[Frobenius](https://en.wikipedia.org/wiki/Frobenius_normal_form)** | Any matrix over a field, similarity | DFT, Hartley, NTT | The cyclic shift is $K[x]/(x^N-1)$ |
| **[Wedderburn](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem)** | The group algebra $\mathbb{C}[G]$ | Fourier on a finite group, Peter–Weyl | $L(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$ |
| **[Jordan](https://en.wikipedia.org/wiki/Jordan_normal_form)** | Matrices over $\mathbb{C}$, similarity | Where the method fails: a repeated pole of a Laplace transform inverts to $t^k e^{\lambda t}$, a Jordan block, which is [resonance](https://en.wikipedia.org/wiki/Resonance) | Where [complete reducibility](https://en.wikipedia.org/wiki/Maschke%27s_theorem) fails, as for $\mathbb{R}$ acting on the plane by shears |

### Children of stage three

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **[Jacobi Transform](https://en.wikipedia.org/wiki/Jacobi_polynomials)** | $[-1, 1]$; for integer parameters, the $(m', m)$ entries of the irreducible representations of $SU(2)$, the [Wigner $d$-matrices](https://en.wikipedia.org/wiki/Wigner_D-matrix#Wigner_(small)_d-matrix), [complete by Peter–Weyl](https://en.wikipedia.org/wiki/Wigner_D-matrix#Orthogonality_relations); $\alpha = \beta = 0$ is Legendre[^polynomials] | $(1-x)^\alpha (1+x)^\beta P_n^{(\alpha,\beta)}(x)$ | Angular momentum in quantum mechanics | Peter–Weyl |

## Stage four: equivariant maps, symmetry without a diagonal

Three rows remain, and in each the group is still there but the diagonal is gone. What is left is an [equivariant map](https://en.wikipedia.org/wiki/Equivariant_map), a map between two representations of one group that commutes with the action; a diagonalizing change of basis is the special case where the target is a sum of one-dimensional pieces, and here the target is something else.

**Radon: between two homogeneous spaces.** The **Radon transform** carries functions on points to functions on lines, and the rigid motions act on both, so it is an equivariant map from $L(G/K)$ to $L(G/H)$, with $K$ and $H$ the stabilizers of a point and of a line. Such maps are exactly the functions on $G$ invariant under $K$ on the left and $H$ on the right, and a Radon transform is an incidence relation read as such a function.[^radon]

**Wavelets and Gabor: into the regular representation.** The **wavelet** and **Gabor** transforms keep a group, the affine and Heisenberg groups, but give up diagonalization altogether. Each pairs $f$ with the translates $\pi(g)\psi$ of a chosen window $\psi$, $W_\psi f(g) = \langle f, \pi(g)\psi\rangle$, and that map is equivariant from $\pi$ into the [regular representation](https://en.wikipedia.org/wiki/Regular_representation) on $L^2(G)$. What survives of the diagonal is energy: an [admissibility](https://en.wikipedia.org/wiki/Continuous_wavelet_transform) condition on $\psi$ makes the map an isometry, which is what it means for $\pi$ to be a [square-integrable representation](https://en.wikipedia.org/wiki/Square-integrable_representation).[^wavelet] Compare the Gelfand pair, where the transform paired $f$ with the translates of the one $K$-fixed vector: here $\psi$ is fixed by no stabilizer at all. Dropping that invariance costs the diagonal, since there is no commutative algebra left to diagonalize, and leaves the isometry, which never depended on characters.

### Children of stage four

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **Finite Radon Transform** | $S_n$ acting on $k$-subsets and $j$-subsets of $\{1, \dots, n\}$, $j < k \le n/2$; onto, with an explicit right inverse[^radon] | Incidence: $1$ when the $k$-subset contains the $j$-subset | Ranked and partially ranked data | Radon |
| **[Discrete Wavelet Transform](https://en.wikipedia.org/wiki/Discrete_wavelet_transform)** | The affine group on the lattice $a = a_0^m$, $b = n b_0 a_0^m$, the family asked to be a frame[^finite] | $a_0^{-m/2} \overline{\psi(a_0^{-m} t - n b_0)}$ | JPEG 2000, multiresolution analysis | Wavelet |

## Where the thread ends

The four stages account for the twelve rows and their children. Two things that carry the name "transform", or are treated alongside them, are outside, each for a different reason.

**Operators a transform diagonalizes.** The [Hilbert transform](https://en.wikipedia.org/wiki/Hilbert_transform) (1905) is convolution with $1/\pi t$ on the line, so it commutes with translation and the Fourier transform diagonalizes it, as multiplication by $-i \mathrm{sgn} \xi$.[^hilbert] The [Stieltjes transform](https://en.wikipedia.org/wiki/Stieltjes_transformation) is the Laplace transform applied twice, $\int_0^\infty f(t)\,dt/(t+x)$; its kernel depends on $t$ and $x$ only through the ratio $t/x$, up to the factor $1/x$, so it commutes with dilations and the Mellin transform diagonalizes it, as multiplication by $\pi/\sin \pi p$.[^stieltjes] The [Weyl fractional integral](https://en.wikipedia.org/wiki/Riemann%E2%80%93Liouville_integral) is of the same kind, a Mellin multiplier.[^stieltjes] These are not changes of basis but the kind of operator a change of basis is *for*, and that is why they have no row.

**No basis at all.** A transform also counts. Let $A \subset \mathbb Z_N$, $N$ odd, have density $\alpha$; the fraction of three-term [arithmetic progressions](https://en.wikipedia.org/wiki/Arithmetic_progression) $x + y = 2z$ with all three terms in $A$ is $\sum_r \hat A(r)^2 \hat A(-2r)$, which is $\alpha^3$, the random share, plus an error of at most $\alpha \max_{r \ne 0} \lvert \hat A(r) \rvert$; so either $A$ has its random share or a character correlates with it, and iterating on the progressions where that character is nearly constant is [Roth's theorem](https://en.wikipedia.org/wiki/Roth%27s_theorem_on_arithmetic_progressions) of 1953.[^roth] The [Gowers norms](https://en.wikipedia.org/wiki/Gowers_norm) (1998) are where this stops. On $\mathbb Z_N$ with $N$ odd the function $e^{2\pi i x^2/N}$ has every Fourier coefficient of modulus $N^{-1/2}$, as flat as Plancherel allows, yet it and three companions have four-term progression count $1$, the largest possible: the transform is blind to the quadratic phases. There are $N^2$ of them against $N$ characters, so they are no basis, and no quadratic transform or inversion formula exists. What survives is the $U^3$ norm, an average over cubes, and an inverse theorem: a function with large $U^3$ norm correlates with a phase built from a two-step [nilpotent group](https://en.wikipedia.org/wiki/Nilpotent_group), a [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) once more.[^gowers] Nothing is being diagonalized, so the thread does not fray there so much as end.

One idea from a first course in linear algebra reaches across two and a half centuries into number theory, tomography, image compression and quantum computation. Representation theory is what one reaches for where it stops, and it works there because diagonalization was one of its tools and never the whole of it.

## Sources

- Lokenath Debnath and Dambaru Bhatta, *Integral Transforms and Their Applications*, 3rd ed., CRC Press, 2015.
- Audrey Terras, *Fourier Analysis on Finite Groups and Applications*, LMS Student Texts 43, Cambridge, 1999.
- Walter Rudin, *Fourier Analysis on Groups*, Interscience.
- Elias M. Stein and Guido Weiss, *Introduction to Fourier Analysis on Euclidean Spaces*, Princeton Mathematical Series 32, Princeton, 1971.
- Paul R. Halmos, *Finite-Dimensional Vector Spaces*, 2nd ed., Springer UTM.
- Benjamin Steinberg, *Representation Theory of Finite Groups: An Introductory Approach*, Springer Universitext, 2012.
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Harmonic Analysis on Finite Groups*, Cambridge, 2008 (cited as CST 2008).
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Discrete Harmonic Analysis*, Cambridge, 2018 (CST 2018).
- Persi Diaconis, *Group Representations in Probability and Statistics*, IMS Lecture Notes 11, 1988.
- Michael A. Nielsen and Isaac L. Chuang, *Quantum Computation and Quantum Information*, Cambridge.
- George W. Mackey, *Harmonic analysis as the exploitation of symmetry: a historical survey*, Bull. AMS 3 (1980), 543–698.
- Louis Auslander and Richard Tolimieri, *Is computing with the finite Fourier transform pure or applied mathematics?*, Bull. AMS (N.S.) 1 (1979), no. 6, 847–897 (cited as AT).
- W. T. Gowers, *Generalizations of Fourier analysis, and how to apply them*, Bull. AMS (N.S.) 54 (2017), no. 1, 1–44.


[^dates]: Clairaut 1754, Gauss 1805 and Cooley–Tukey 1965: Terras, pp. xv–xvi and 30–31; Cooley–Tukey's own paragraphs are quoted in AT, §II.1, p. 871. Laplace in the 1780s, Fourier 1822: Debnath–Bhatta, §1.1.

[^series]: Fourier's memoir of 1807: Terras, p. 30; Mackey, p. 566. The three classical groups $\mathbb{R}$, $\mathbb{T}$, $\mathbb{Z}$, their duals and the three transforms, including $\hat f(e^{i\alpha}) = \sum_n f(n) e^{-in\alpha}$ for $G = \mathbb{Z}$: Rudin, §1.2.7, pp. 12–13; discrete and compact groups are dual: Theorem 1.2.5, p. 9.

[^hankel]: Debnath–Bhatta, §1.1 for the history and Theorem 7.3.4 for $\mathcal H_n[\nabla^2 f] = -\kappa^2 \tilde f$. Stein–Weiss, Chapter IV, Theorem 1.1, p. 135 (the Fourier transform commutes with orthogonal transformations) and Corollary 1.2 (the transform of a radial function is radial); with Rudin, Theorem 1.2.4(b) (convolution to multiplication), this is the commutativity claimed.

[^legendre]: Terras, p. 180: for $G = O(3)$, $K = O(2)$ the spherical functions are the Legendre polynomials in $\cos\theta$; p. 341 for the 1780s. Debnath–Bhatta, (14.2.1), for Churchill's 1954 definition $\tilde f(n) = \int_{-1}^{1} P_n(x) f(x)\,dx$ and §14.4 for potential theory. The Hankel formula: Stein–Weiss, Chapter IV, Theorem 3.3, p. 155; the other orders, Theorem 3.10, p. 158, $\hat f(x) = F_0(\lvert x \rvert)P(x)$ with $F_0(r) = 2\pi i^{-k} r^{-(n+2k-2)/2}\int_0^\infty f_0(s) J_{(n+2k-2)/2}(2\pi rs) s^{(n+2k)/2}\,ds$.

[^finite]: Debnath–Bhatta: finite Fourier sine and cosine transforms, (10.2.1) and (10.2.4); sine and cosine transforms from the odd and even cases of the Fourier integral, (2.2.8)–(2.2.9) and (2.13.1); finite Laplace transform, (11.2.1); finite Hankel transform, p. 502 and Definition 13.2.1; discrete wavelet transform, (19.3.1) and the frame condition following it.

[^hadamard]: Terras, p. xvi (Hadamard transform = Fourier on $(\mathbb{Z}/2)^n$) and p. 174 (Walsh functions as reordered Hadamard rows).

[^mellin]: Debnath–Bhatta, §8.1 for the Riemann–Cahen–Mellin priority and §8.2 for the substitution $x = e^\xi$.

[^frobenius]: Terras, p. 237, for Dedekind's letter and 1897; Mackey, p. 695, for Weyl thirty years later, and pp. 603–604 for the Peter–Weyl theorem of 1927.

[^hilbert]: Debnath–Bhatta, Theorem 9.3.1(f): $\mathcal{F}[\mathcal{H}f] = (-i \mathrm{sgn} k) \mathcal{F}[f]$.

[^stieltjes]: Debnath–Bhatta, (9.7.1)–(9.7.3), the Stieltjes transform as the Laplace transform of the Laplace transform; (9.8.2), $S\{f(at)\} = \tilde f(az)$; (9.7.11) and Example 9.7.2, the Mellin form with $g(u) = (1+u)^{-1}$, $\mathcal{M}\{\tilde f\}(p) = \tilde f(p)\tilde g(1-p)$ and $\tilde g(1-p) = \pi\,\mathrm{cosec}(\pi p)$. Weyl fractional integral: (5.3.17) and Definition 8.5.1.

[^gegenbauer]: Stein–Weiss, Chapter IV §2: zonal harmonics, p. 143, and Lemma 2.8(c); Theorem 2.12, pp. 146–147, a spherical harmonic of degree $k$ constant on the parallels orthogonal to $e$ is a multiple of the zonal harmonic $Z_e^{(k)}$; Theorem 2.14, p. 149, $Z_{y'}^{(k)}(x') = c_{k,n} P_k^\lambda(x' \cdot y')$ with $\lambda = (n-2)/2$, the Gegenbauer polynomial of p. 148. The Gegenbauer transform: Debnath–Bhatta, (15.5.4), the case $\alpha = \beta = \nu - \tfrac12$ of the Jacobi transform.

[^polynomials]: Jacobi transform: Debnath–Bhatta, (15.2.1), $\int_{-1}^{1} (1-x)^\alpha (1+x)^\beta P_n^{(\alpha,\beta)}(x) F(x)\,dx$, reducing to Legendre at $\alpha = \beta = 0$ (p. 533). With $x = \cos\beta$, the Haar measure $\sin\beta\,d\beta = -dx$ and $\sin^2\tfrac\beta2 = \tfrac{1-x}{2}$, $\cos^2\tfrac\beta2 = \tfrac{1+x}{2}$ turn the orthogonality of the $d$-matrices into the Jacobi weight. Laguerre transform: Debnath–Bhatta, (16.2.1), $\int_0^\infty e^{-x} x^\alpha L_n^\alpha(x) f(x)\,dx$.

[^radon]: Debnath–Bhatta, §1.3, for Radon in 1917. CST 2008, §6.5, Theorem 6.5.2, for the finite Radon transform and its right inverse, and Exercise 4.2.5 for equivariant maps as bi-invariant functions.

[^wavelet]: Debnath–Bhatta, §1.3 for Gabor (1946) and Morlet–Grossmann (1982–84); Definition 19.2.1 and Theorem 19.2.2 for admissibility and the Parseval relation. Equivariance is the identity $W_\psi(\pi(h)f)(g) = \langle f, \pi(h^{-1}g)\psi\rangle$ for unitary $\pi$. The comparison with the spherical function $\langle u,\rho(g)u\rangle$ (CST 2008, Cor. 4.6.4) is the present author's.

[^hsp]: Nielsen–Chuang, p. 221 (the amplitudes of a state cannot be read out, so the quantum Fourier transform is not a fast FFT: its output is read as a measurement of which irreducible representation the state lies in) and §5.4.3 (the hidden subgroup problem, with Simon's algorithm as the case $(\mathbb Z_2)^n$ and Shor's as the case $\mathbb{Z}$).

[^halmos]: Halmos, §79–80 (spectral theorem, self-adjoint and then normal), §84 Exercise 6 (simultaneous diagonalization), §81 (real orthogonal transformations as plane rotations).

[^mackey]: Mackey, §2 (pp. 547–548) for translation becoming multiplication, §9 (pp. 568–575) for differentiation becoming multiplication, the potential and heat-kernel formulas, first obtained by other means (pp. 570–571), and the sphere (p. 574).

[^rudin]: Rudin, Theorem 1.2.2 and p. 9 (the Fourier transform as the Gelfand transform of $L^1(G)$), Theorem 1.2.4 (convolution) and Chapter 1 generally; for finite groups, Steinberg, Chapter 5.

[^dct]: CST 2008, Appendix 1: the sixteen DCT/DST bases as eigenvectors of path-graph operators obtained by folding under a reflection; the DCT-2 from the involution $k \mapsto 2n-1-k$ on $C_{2n}$, in the paragraph headed "DCT-2".

[^dftspectrum]: Debnath–Bhatta, Appendix A-6, (A-6.11)–(A-6.13), for the Hermite functions as an orthogonal basis of $L^2(\mathbb{R})$ with $\mathcal{F}h_n = (-i)^n h_n$; the Hermite transform, (17.2.1), is $\int e^{-x^2} H_n(x) F(x)\,dx$, the expansion of $e^{-x^2/2}F$ in the $h_n$. For the DFT: CST 2018, Proposition 4.1.2 ($F^4 = I$) and Theorem 4.3.1 (multiplicities $m+1, m, m, m-1$ for $N = 4m$); AT, Theorem 1.1.2, p. 855, for the trace as a Gauss sum.

[^gelfandpair]: CST 2008, Theorem 4.4.2, Corollary 4.6.4 and Proposition 4.7.2; Steinberg, Example 7.3.5, for $(G,\{1\})$.

[^wedderburn]: Steinberg, Theorem 5.5.6; CST 2008, Theorem 9.5.4, for $(G \times G, \Delta G)$.

[^diaconis]: Diaconis, Chapter 3B Lemma 1 (upper bound lemma, with the norm as defined there), 3C Theorem 2 ($\mathbb Z_p$), 3D Theorem 5 (random transpositions); conjugacy classes as canonical forms, p. 14. Cayley graphs: Steinberg, Theorem 5.4.10 (abelian) and Exercise 5.12 (class functions); the block statement is Theorem 5.5.6 read on $L(G)$.

[^laplace]: Debnath–Bhatta, §1.1, p. 2 (why the Laplace transform is easier); Mackey, pp. 550–551 (Laplace's generating functions of 1782, $t^n$ as characters of $\mathbb{Z}$, the difference equation becoming algebraic).

[^fft]: CST 2018, §10.7 and Exercise 10.7.3 (Diaconis–Rockmore, with Cooley–Tukey as the case $K = \mathbb Z_m$); §5.4 for Rader, and AT, §III.2, pp. 882–883.

[^roth]: Gowers, §3, pp. 4–6, Lemma 3.2 and the iteration.

[^gowers]: Gowers, §7, p. 17 (the example), §8, p. 18 ($n^2$ phases, no basis), §11.1, p. 28 (no transform), Theorem 11.2 and pp. 25–27 (inverse theorem, nilsequences, the Heisenberg group); the 1998 paper is his reference [17].
