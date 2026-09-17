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

An [integral transform](https://en.wikipedia.org/wiki/Integral_transform) (resp. discrete transform) $\mathcal{T}$ is a **change of basis**: it re-expresses a function (resp. sequence) $f$ on a domain $D$ in terms of a different set of basis functions. For a kernel $k(t, u)$,

$$(\mathcal{T}f)(u) = \int_{D} f(t)\, k(t, u)\, dt \quad \Big(\text{resp.} \sum_{t \in D} f(t)\, k(t, u)\Big)$$

The domain can be an interval, a ring of $N$ points, the positive reals under multiplication, the surface of a sphere. What every such domain carries is a symmetry, a [group](https://en.wikipedia.org/wiki/Group_(mathematics)) $G$ acting on $D$ under which $D$ looks the same from any of its points. The third column of the table below names it for each transform.

From Laplace in the 1780s to wavelets in the 1980s, the zoo is one idea repeated, and the idea comes from a first course in linear algebra.

> A transform is the change of basis that makes the symmetry of its domain act diagonally. The variety of transforms is the variety of domains and their symmetries, and the thread frays in one predictable order as the symmetry becomes less commutative: abelian group, then Gelfand pair, then non-abelian group, then an equivariant map, where no diagonal is left at all.

The table is in the order of history, and its last column assigns each row to one of the four stages of the sentence. The sections after the table take the stages in order. Every other transform in the zoo is a child of one of these twelve rows and is listed, in the same columns, in a table at the end of its parent's stage.

## The transforms in chronological order

| Year | Transform | Domain / symmetry ($G$) | Kernel | Primary application | Stage |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1754** | **[Discrete Fourier Transform (DFT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)** | [Cyclic group](https://en.wikipedia.org/wiki/Cyclic_group) $(\mathbb Z_N, +)$ | $e^{-2\pi i jk/N}$ | Orbit determination, and thereafter the whole of digital signal processing[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1782** | **[Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform)** | $(\mathbb{R}, +)$ on functions supported in $[0,\infty)$, the character $e^{-st}$ continued to $\Re s > 0$ | $e^{-st}$ | Control theory, ODE stability, circuit analysis[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1782** | **[Spherical Harmonic Transform](https://en.wikipedia.org/wiki/Spherical_harmonics)** | 2-sphere $S^2 = SO(3)/SO(2)$, the [rotation group](https://en.wikipedia.org/wiki/3D_rotation_group) modulo rotations about an axis | $\overline{Y_\ell^m(\theta,\varphi)}$ | Geopotential models, atomic orbitals, CMB analysis[^legendre] | [Gelfand pair (2)](#stage-two-gelfand-pairs) |
| **1807** | **[Fourier Series](https://en.wikipedia.org/wiki/Fourier_series)** | [Circle group](https://en.wikipedia.org/wiki/Circle_group) $\mathbb{T} = \mathbb{R}/2\pi\mathbb{Z}$ | $e^{-in\theta}$ | Heat conduction in a bar, vibrating strings, every periodic signal[^series] | [abelian (1)](#stage-one-abelian-groups) |
| **1822** | **[Continuous Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)** | Real line $(\mathbb{R}, +)$ | $e^{-i\omega t}$ | Heat conduction, wave mechanics, quantum theory[^dates] | [abelian (1)](#stage-one-abelian-groups) |
| **1875** | **[Hankel Transform](https://en.wikipedia.org/wiki/Hankel_transform)** | $SO(n)$-invariant functions on $\mathbb{R}^n$: the [Euclidean motion group](https://en.wikipedia.org/wiki/Euclidean_group) of $\mathbb{R}^n$ modulo its rotations, a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) | $t J_\nu(ut)$ | Axisymmetric boundary value problems, optics, acoustics[^hankel] | [Gelfand pair (2)](#stage-two-gelfand-pairs) |
| **1896** | **[Mellin Transform](https://en.wikipedia.org/wiki/Mellin_transform)** | Multiplicative reals $(\mathbb{R}^+, \times)$ | $t^{s-1}$ | Analytic number theory, Dirichlet series, asymptotics[^mellin] | [abelian (1)](#stage-one-abelian-groups) |
| **1897** | **[Fourier Transform on Finite Groups](https://en.wikipedia.org/wiki/Fourier_transform_on_finite_groups)** | Finite groups: [$S_n$](https://en.wikipedia.org/wiki/Symmetric_group), [$D_n$](https://en.wikipedia.org/wiki/Dihedral_group), [$GL_2(\mathbb F_q)$](https://en.wikipedia.org/wiki/General_linear_group) | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Representation theory, card shuffling, spectral graph theory[^frobenius] | [non-abelian (3)](#stage-three-non-abelian-groups) |
| **1917** | **[Radon Transform](https://en.wikipedia.org/wiki/Radon_transform)** | Lines in $\mathbb{R}^2$, affine hyperplanes in $\mathbb{R}^n$ | $\delta(u - \langle x, \theta \rangle)$ | CT and PET tomography, seismic imaging[^radon] | [equivariant (4)](#stage-four-equivariant-maps) |
| **1927** | **[Peter-Weyl Transform](https://en.wikipedia.org/wiki/Peter%E2%80%93Weyl_theorem)** | [Compact Lie groups](https://en.wikipedia.org/wiki/Compact_group) $SO(3)$, [$SU(2)$](https://en.wikipedia.org/wiki/Special_unitary_group) | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Angular momentum, particle physics, molecular replacement[^frobenius] | [non-abelian (3)](#stage-three-non-abelian-groups) |
| **1946** | **[Gabor Transform / STFT](https://en.wikipedia.org/wiki/Short-time_Fourier_transform)** | Time-frequency plane, the [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) | $\overline{g(t-b)} e^{-i\omega t}$ | Spectrograms, speech, time-frequency analysis[^wavelet] | [equivariant (4)](#stage-four-equivariant-maps) |
| **1984** | **[Wavelet Transform](https://en.wikipedia.org/wiki/Continuous_wavelet_transform)** | The [affine](https://en.wikipedia.org/wiki/Affine_group), or "$ax+b$", group | $a^{-1/2} \overline{\psi((t-b)/a)}$ | JPEG 2000, denoising, LIGO analysis[^wavelet] | [equivariant (4)](#stage-four-equivariant-maps) |

## What a transform does

The idea is [diagonalization](https://en.wikipedia.org/wiki/Diagonalizable_matrix). A unitary change of basis $A \mapsto U A U^{\ast}$ brings every [normal](https://en.wikipedia.org/wiki/Normal_matrix) operator to diagonal form; that is the [spectral theorem](https://en.wikipedia.org/wiki/Spectral_theorem).[^halmos] An integral transform is the $U$. Let $\tau_a$ be translation by $a$ on the real line, $(\tau_a f)(t) = f(t - a)$, and $\mathcal{F}$ the Fourier transform. Then

$$\mathcal{F} \tau_a \mathcal{F}^{-1} = \text{multiplication by } e^{-i a \xi}.$$

A multiplication operator rescales its input point by point, as a diagonal matrix rescales each coordinate. So $\mathcal{F}$ makes translation diagonal, and with it everything that commutes with translation, since [commuting normal operators](https://en.wikipedia.org/wiki/Commuting_matrices) share an eigenbasis: $d/dt$ becomes multiplication by $i\xi$, and every [convolution](https://en.wikipedia.org/wiki/Convolution) becomes multiplication by the transform of its kernel.[^halmos] This is what a transform is used for. A differential equation with constant coefficients becomes algebraic, and its solution comes back as a convolution of the data with a fixed kernel; the Coulomb potential and the heat kernel are the two classical cases, both found before the transform that explains them.[^mackey]

**What "diagonal" means.** One point has to be fixed before the groups get bigger, because the matrix picture misleads in one respect. Translation on $\mathbb{R}$ has no eigenvectors in [$L^2$](https://en.wikipedia.org/wiki/Lp_space#Hilbert_spaces): $e^{i\xi t}$ is bounded but not square-integrable. So there is no eigenbasis, and yet the display above is exact. What it says is that $\mathcal{F}$ carries $\tau_a$ to a multiplication operator, and that is the form the spectral theorem takes on an infinite-dimensional space: a normal operator is unitarily equivalent to multiplication by a function on some $L^2(\mu)$, a diagonal matrix being the case where $\mu$ is counting measure on $N$ points ([multiplication-operator form](https://en.wikipedia.org/wiki/Spectral_theorem#Multiplication_operator_version)). Throughout this post "diagonal" means this: *after the transform, the operator is a multiplication*. An eigenbasis exists when the spectrum is discrete, on a finite group, where the transform is an $N \times N$ unitary matrix and the first course applies verbatim, and on a compact group; on $\mathbb{R}$ the eigenfunctions $e^{i\xi t}$ exist but are not vectors of the space, and the diagonal is the multiplication.

## Stage one: abelian groups

**The setting.** $G$ is a [locally compact abelian group](https://en.wikipedia.org/wiki/Locally_compact_abelian_group) with [Haar measure](https://en.wikipedia.org/wiki/Haar_measure) $dg$; when $G$ is finite, $dg$ is counting measure and every integral below is a sum. $L^2(G)$ is the space of square-integrable functions on $G$ with $\langle f, h \rangle = \int_G f \bar h\, dg$; for finite $G$ it is the space of all functions $G \to \mathbb{C}$. Translation by $g$ is $(\lambda(g) f)(x) = f(g^{-1} x)$, so that on $\mathbb{R}$, $\lambda(a) = \tau_a$; and convolution is $(f \ast h)(x) = \int_G f(g)\, h(g^{-1}x)\, dg$. The operators on $L^2(G)$ that commute with every translation are the convolutions $f \mapsto f \ast h$.[^setting]

**What breaks.** Nothing yet. This is the stage the sentence describes verbatim, and the other three are measured against it.

**What replaces the character.** Nothing needs to; this is the stage that has them. The convolutions commute with one another, so one change of basis makes them all multiplications, and the common eigenfunctions are the **characters**, the continuous homomorphisms $\chi\colon G \to \mathbb{T}$: $\chi \ast h = \hat h(\chi)\, \chi$, where $\hat h(\chi)$ is the transform below.[^rudin] The characters are bounded functions, in $L^2(G)$ only when $G$ is compact, which is the point of the paragraph on what "diagonal" means. The group decides the kernel, and the kernel column of the table is the characters written out. In symbols,

$$\hat f(\chi) = \int_G f(g)\, \overline{\chi(g)}\, dg, \qquad \widehat{f \ast h} = \hat f\, \hat h.$$

The characters form the dual group $\hat G$, and the transform is an isometry $L^2(G) \to L^2(\hat G)$, the [Plancherel theorem](https://en.wikipedia.org/wiki/Plancherel_theorem), carrying $f \mapsto f \ast h$ to multiplication by $\hat h$: that is the diagonalization, in the sense fixed above, and the second half of the display is its formula. Further, $\hat{\hat G} = G$ ([Pontryagin duality](https://en.wikipedia.org/wiki/Pontryagin_duality)), and in the language of Banach algebras the transform is the [Gelfand transform](https://en.wikipedia.org/wiki/Gelfand_representation) of $L^1(G)$.[^rudin]

**DFT.** $G = \mathbb Z_N$, self-dual, with characters $\chi_k(j) = e^{2\pi i jk/N}$. The transform is the $N \times N$ unitary matrix $N^{-1/2}(e^{-2\pi i jk/N})_{k,j}$, and the first course applies without change.

**Fourier series.** $G = \mathbb{T}$, with dual $\mathbb{Z}$ and characters $e^{in\theta}$; the group is compact and the spectrum is discrete. The transform in the other direction, on $G = \mathbb{Z}$ with dual $\mathbb{T}$, is the Fourier series read backwards, $\hat f(e^{i\theta}) = \sum_n f(n) e^{-in\theta}$.[^series]

**Fourier transform.** $G = \mathbb{R}$, self-dual, with characters $e^{i\omega t}$; the group is neither compact nor discrete, and neither is the spectrum: there is no eigenbasis, and the transform diagonalizes translation in the multiplication sense only.

**Mellin.** $G = (\mathbb{R}^+, \times)$. The substitution $t = e^{\xi}$ carries it to $(\mathbb{R}, +)$ and the kernel to $t^{s-1}\,dt = e^{s\xi}\,d\xi$, so the Mellin transform is the Fourier transform of $f(e^\xi)$ at the complex frequency $s$; the unitary characters are the $t^{i\omega}$, on the line $\Re s = 0$.[^mellin]

**Laplace.** $G = \mathbb{R}$ on functions supported in $[0, \infty)$, with the character $e^{-i\omega t}$ continued to the complex frequency $s$, $\Re s > 0$. The gain is that $e^{-st}$ decays and the result is analytic in $s$; the cost is orthogonality, since the $e^{-st}$ for real $s$ are not orthogonal and there is no Plancherel formula on the real $s$-axis. The isometry holds line by line: on $\Re s = c$ the Laplace transform of $f$ is the Fourier transform of $e^{-ct} f$.[^laplace]

### Children of stage one

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **[Fast Fourier Transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform)** | $(\mathbb Z_N, +)$, the sum split along a subgroup; any finite group with a chain of subgroups; Rader for prime $N$ | The DFT kernel, rearranged | Everything the DFT is used for, in $N \log N$ operations[^fft] | DFT |
| **[Walsh–Hadamard Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | $(\mathbb Z_2)^n$, the same construction on another finite abelian group | $(-1)^{\langle x, y \rangle}$ | Error-correcting codes, Simon's algorithm, the hidden subgroup problem on $(\mathbb Z_2)^n$[^hadamard] | DFT |
| **[Hartley Transform](https://en.wikipedia.org/wiki/Hartley_transform)** | $(\mathbb Z_N, +)$ or $(\mathbb{R}, +)$ over the real field; see the field table below | $\cos ut + \sin ut$ | Signal processing without complex arithmetic | DFT |
| **[Number-Theoretic Transform (NTT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_over_a_ring#Number-theoretic_transform)** | $(\mathbb Z_N, +)$ with $\omega$ a root of unity in $\mathbb F_q^\times$; see the field table below | $\omega^{jk} \bmod q$ | Exact integer convolution | DFT |
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

### Changing the field: Hartley and NTT

Two of the children keep $G = \mathbb Z_N$ and change the [field](https://en.wikipedia.org/wiki/Field_(mathematics)) of scalars from $\mathbb{C}$ to a field $\mathbb{F}$. Over $\mathbb{F}$ the [circulant matrices](https://en.wikipedia.org/wiki/Circulant_matrix) are $\mathbb{F}[x]/(x^N-1)$, the cyclic shift is the [companion matrix](https://en.wikipedia.org/wiki/Companion_matrix) of $x^N - 1$, and the [Frobenius normal form](https://en.wikipedia.org/wiki/Frobenius_normal_form) says how far the shift can be reduced: to one block for each irreducible factor of $x^N - 1$ over $\mathbb{F}$.

| Field $\mathbb{F}$ | How $x^N - 1$ factors over $\mathbb{F}$ | Best canonical form of the shift | Transform |
| :--- | :--- | :--- | :--- |
| $\mathbb{C}$ | $N$ distinct linear factors | Diagonal | **DFT** |
| $\mathbb{R}$ | $x - 1$, also $x + 1$ when $N$ is even, and quadratics $x^2 - 2\cos(2\pi k/N) x + 1$ | $2 \times 2$ rotation blocks | **Hartley** |
| $\mathbb F_q$, the [finite field](https://en.wikipedia.org/wiki/Finite_field) with $q$ elements | $N$ distinct linear factors exactly when $N \mid q-1$ | Diagonal over $\mathbb F_q$ | **NTT** |

The middle row is the real spectral theorem: no real basis separates a conjugate pair of eigenvalues, so the Hartley kernel $\cos\nu x + \sin\nu x$ pairs $\nu$ with $-\nu$, and no real transform does better.[^halmos] The last row says that a change of field costs nothing provided $\mathbb F_q^\times$, a cyclic group of order $q - 1$, contains an element of order $N$.

## Stage two: Gelfand pairs

**The setting.** As in stage one, except that $G$ is a [locally compact group](https://en.wikipedia.org/wiki/Locally_compact_group), not necessarily abelian, and the domain is not $G$ but a space $X$ on which $G$ acts [transitively](https://en.wikipedia.org/wiki/Group_action#Transitivity_properties). $K$ is the [stabilizer](https://en.wikipedia.org/wiki/Group_action#Fixed_points_and_stabilizer_subgroups) of a chosen base point, so that $X = G/K$ is a [homogeneous space](https://en.wikipedia.org/wiki/Homogeneous_space): $S^2 = SO(3)/SO(2)$, and $\mathbb{R}^n = G/K$ with $G$ the Euclidean motion group and $K = SO(n)$, so that the radial functions are the $K$-invariant functions on $X$. $G$ acts on $L^2(X)$ by the formula of stage one, $(\lambda(g) f)(x) = f(g^{-1} x)$. A [unitary representation](https://en.wikipedia.org/wiki/Unitary_representation) $\pi$ of $G$ on a Hilbert space $V_\pi$ is [irreducible](https://en.wikipedia.org/wiki/Irreducible_representation) when $V_\pi$ has no proper nonzero closed invariant subspace, and $d_\pi = \dim V_\pi$; a character is the case $d_\pi = 1$.

**What breaks.** The domain is no longer a group. The **Hankel transform** acts on radial functions on $\mathbb{R}^n$ and the **spherical harmonic transform** on $S^2$; the sphere cannot be made a group, and $SO(3)$, which acts on it, has no invariant one-dimensional space of functions but the constants.[^mackey] So there are no characters. Yet both transforms are diagonal: the Hankel transform turns the radial Laplacian into multiplication by $-\kappa^2$,[^hankel] and the spherical harmonics are eigenfunctions of the Laplacian on the sphere.[^legendre]

**What replaces the character.** The operators on $L^2(X)$ commuting with every $\lambda(g)$ form an algebra, and $(G, K)$ is a Gelfand pair when that algebra is commutative; [symmetric spaces](https://en.wikipedia.org/wiki/Symmetric_space) are the motivating examples. When it is, three things hold at once. The commuting operators diagonalize simultaneously, as in stage one. $L^2(X)$ splits into irreducible pieces $V_\pi$, no piece repeated: a direct sum when $G$ is compact, as for $S^2$, where the spectrum is discrete, and with a continuous spectrum for $\mathbb{R}^n$, as on $\mathbb{R}$. And each $V_\pi$ contains, up to scale, one $K$-fixed unit vector $u_\pi$; read as a function on $X$ it is the [spherical function](https://en.wikipedia.org/wiki/Zonal_spherical_function) of the piece, and it plays the part of the character:

$$\phi_\pi(gK) = \langle u_\pi, \pi(g) u_\pi \rangle, \qquad \hat f(\pi) = \langle f, \phi_\pi \rangle \quad \text{for } K\text{-invariant } f.$$

The $\phi_\pi$ are the multiplicative functionals of the commutative algebra, exactly as the characters are for $L^1(G)$; and for $f \in L^2(X)$ not $K$-invariant, $\langle f, \pi(g) u_\pi\rangle$ as a function of $gK$ is a multiple of the projection of $f$ onto $V_\pi$.[^gelfandpair] Stage one is the case $K = \{1\}$: $(G, \{1\})$ is a Gelfand pair if and only if $G$ is abelian, and the spherical functions are then the characters.[^gelfandpair] The hypothesis was never commutativity of $G$ but commutativity of the operators commuting with $G$, equivalently no repeated piece. This is the first place the transforms need representation theory, and for one job: to say when a transform is still diagonal.

**Spherical harmonic transform.** $(G, K) = (SO(3), SO(2))$, $X = S^2$. The pieces $V_\ell$ are the spherical harmonics of degree $\ell$, the spherical function of $V_\ell$ is the [Legendre polynomial](https://en.wikipedia.org/wiki/Legendre_polynomials) $P_\ell(\cos\theta)$ with $\theta$ the angle from the fixed axis, and the transform of $f \in L^2(S^2)$ is its expansion in the $Y_\ell^m$; on zonal $f$ it is the integral against $P_\ell$.[^legendre] For $(SO(n), SO(n-1))$ on $S^{n-1}$ the Legendre polynomials become [Gegenbauer polynomials](https://en.wikipedia.org/wiki/Gegenbauer_polynomials).[^gegenbauer]

**Hankel transform.** $G = \mathbb{R}^n \rtimes SO(n)$, $K = SO(n)$, $X = \mathbb{R}^n$; the spectrum is continuous, so "diagonal" is again the multiplication sense. Here the commutativity is elementary: the operators commuting with the motion group are convolutions by radial kernels, and the Fourier transform makes them multiplications by radial functions.[^hankel] The Hankel transform of order $(n-2)/2$ is the Fourier transform on $\mathbb{R}^n$ restricted to radial functions, which is where the [Bessel function](https://en.wikipedia.org/wiki/Bessel_function) in the kernel comes from. The other orders in the table come from the other pieces of $L^2(\mathbb{R}^n)$: on $f_0(\lvert x \rvert) P(x)$ with $P$ a [harmonic polynomial](https://en.wikipedia.org/wiki/Harmonic_polynomial) of degree $k$, the Fourier transform is $P$ times a Hankel transform of order $k + (n-2)/2$.[^legendre]

### Children of stage two

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **[Legendre Transform](https://en.wikipedia.org/wiki/Legendre_polynomials)** | Zonal functions on $S^2$, those fixed by $SO(2)$: the spherical functions of $(SO(3), SO(2))$[^legendre] | $P_\ell(\cos\theta)$ | Axisymmetric potential problems | Spherical harmonic |
| **[Gegenbauer Transform](https://en.wikipedia.org/wiki/Gegenbauer_polynomials)** | Zonal functions on $S^{n-1}$: the spherical functions of $(SO(n), SO(n-1))$, with $\lambda = (n-2)/2$; $n = 3$ is Legendre[^gegenbauer] | $(1-x^2)^{\lambda - 1/2} P_k^\lambda(x)$ | Potential problems in $n$ dimensions | Spherical harmonic |
| **[Jacobi Transform](https://en.wikipedia.org/wiki/Jacobi_polynomials)** | $[-1, 1]$ with the weight $(1-x)^\alpha(1+x)^\beta$; $\alpha = \beta = \lambda - \tfrac12$ is Gegenbauer and $\alpha = \beta = 0$ is Legendre[^polynomials] | $(1-x)^\alpha (1+x)^\beta P_n^{(\alpha,\beta)}(x)$ | Boundary value problems with the Jacobi weight | Spherical harmonic |
| **[Finite Hankel Transform](https://en.wikipedia.org/wiki/Fourier%E2%80%93Bessel_series)** | $0 < r < a$, the Fourier–Bessel series: compact domain, discrete spectrum[^finite] | $r J_n(r k_i)$ | Vibrating membranes, heat in a cylinder | Hankel |

## Stage three: non-abelian groups

**The setting.** As in stage two, except that the domain is the group again, $X = G$ and $K = \{1\}$, with $G$ finite or a compact Lie group; $\lambda$ and $\ast$ are those of stage one, $\pi$, $V_\pi$, $d_\pi$ those of stage two, and $\chi_\pi = \mathrm{tr}\pi$ is the [character](https://en.wikipedia.org/wiki/Character_theory) of $\pi$, a function on $G$.

**What breaks.** $G$ is not commutative, so $(G, \{1\})$ is not a Gelfand pair: the convolutions $f \mapsto f \ast h$ do not commute with one another and no single eigenbasis exists.

**What replaces the character.** An irreducible representation $\pi$ of dimension $d_\pi$. The transform of $f$ at $\pi$ is a $d_\pi \times d_\pi$ matrix, and convolution becomes matrix multiplication, block by block:

$$\hat f(\pi) = \int_G f(g)\, \overline{\pi(g)}\, dg \in M_{d_\pi}(\mathbb{C}), \qquad \widehat{f \ast h}(\pi) = \hat f(\pi)\, \hat h(\pi),$$

the bar being the entrywise conjugate, so that the kernel is the $\overline{\pi_{ij}(g)}$ of the table.[^wedderburn] For finite $G$ the statement that this is an isomorphism of algebras, $L^2(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$, is [Wedderburn's theorem](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem); stage one is the case where every block is $1 \times 1$.[^wedderburn] Block-diagonal is not diagonal, and the following observation is what makes the transform a diagonalization after all. Let $G \times G$ act on $L^2(G)$ by translating on both sides, $f(g) \mapsto f(g_1^{-1} g g_2)$. Under this larger action the decomposition $L^2(G) = \bigoplus_\pi V_\pi \otimes V_\pi^{\ast}$ has no repeated piece, so $(G \times G, \Delta G)$ with $\Delta G = \{(g, g)\}$ is a Gelfand pair, and its spherical functions are $\chi_\pi / d_\pi$; this is what "character" means for a non-abelian group.[^wedderburn] So the non-abelian transform diagonalizes the two-sided action, and the $d_\pi \times d_\pi$ blocks are what the one-sided action alone can see. The history ran the same way: Frobenius invented representation theory in 1897 to answer a question of Dedekind's about group determinants, and it took until Weyl, thirty years later, for anyone to see that he had extended Fourier analysis from commutative to non-commutative groups.[^frobenius]

**Fourier transform on a finite group.** $G$ finite, the integral a sum. The entries $\pi_{ij}$, over all $\pi$ and all $i, j \le d_\pi$, are an orthogonal basis of $L^2(G)$, and $\lvert G \rvert = \sum_\pi d_\pi^2$; the transform is the unitary $\lvert G \rvert \times \lvert G \rvert$ matrix that expands $f$ in this basis.[^wedderburn]

**Peter–Weyl transform.** $G$ a compact Lie group such as $SO(3)$ or $SU(2)$, the integral against Haar measure. The same statement holds with countably many $\pi$: the matrix coefficients $\pi_{ij}$ are a complete orthogonal system in $L^2(G)$, which is the Peter–Weyl theorem of 1927.[^frobenius]

### Cayley graphs and shuffles

Two uses of the block form. A [Cayley graph](https://en.wikipedia.org/wiki/Cayley_graph) on $G$ has adjacency matrix equal to convolution by the indicator $\delta_S$ of its generating set $S$, so its eigenvalues are those of the blocks $\hat\delta_S(\pi)$, each repeated $d_\pi$ times; when $G$ is abelian, or $S$ is a union of [conjugacy classes](https://en.wikipedia.org/wiki/Conjugacy_class), the blocks are scalars and the eigenvalues are the character sums $\frac{1}{d_\pi}\sum_{s \in S} \chi_\pi(s)$.[^diaconis] And a shuffle is a probability $P$ on $S_n$, $k$ shuffles is $P^{\ast k}$, so $\widehat{P^{\ast k}} = \hat P^k$, and Plancherel bounds the [total-variation distance](https://en.wikipedia.org/wiki/Total_variation_distance_of_probability_measures) $\lVert P^{\ast k} - U \rVert = \max_A \lvert P^{\ast k}(A) - U(A) \rvert$ from the uniform distribution $U$ by a sum over representations:

$$\lVert P^{\ast k} - U \rVert^2 \le \frac14 \sum_{\pi \neq 1} d_\pi \mathrm{tr}\big(\hat P(\pi)^k \hat P(\pi)^{\ast k}\big).$$

For $\mathbb Z_p$, stepping by $\pm 1$, somewhat more than $p^2$ steps are needed. For $S_n$, swapping a random pair each step, $\frac12 n\log n + cn$ shuffles bring the distance below $a e^{-2c}$, while $\frac12 n \log n - cn$ leave it above $\frac1e - o(1)$: the distance drops from a constant to nearly zero in a window of width $O(n)$ around $\frac12 n \log n$, which is the cutoff phenomenon.[^diaconis]

## Stage four: equivariant maps

**The setting.** As in stage two, except that the transform now goes between two different spaces on which $G$ acts. For the Radon transform they are two homogeneous spaces, $X = G/K$ as before and a second one $Y = G/H$, with $H$ the stabilizer of a base point of $Y$; $\lambda_X$ and $\lambda_Y$ are the actions of $G$ on $L^2(X)$ and $L^2(Y)$ by the formula of stage one. For the wavelet and Gabor transforms the source is $L^2(\mathbb{R})$ with $G$ acting by a unitary representation $\pi$, and the target is $L^2(G)$ with the action $\lambda$ of stage one.

**What breaks.** The diagonal. In the three stages so far the transform was a change of basis in which the symmetry acts by scalars, or at worst by blocks; in the three remaining rows the group is still there but the target of the map is not a sum of one-dimensional pieces, and there are no scalars to be found.

**What replaces the character.** Nothing does; what survives is the property that made the character work. A transform $T$ from one of the two spaces to the other is an [equivariant map](https://en.wikipedia.org/wiki/Equivariant_map), one that commutes with the two actions:

$$T\, \lambda_X(g) = \lambda_Y(g)\, T \quad \text{for all } g \in G.$$

Stage one is the case $X = G$, $Y = \hat G$, where $\lambda_Y(g)$ is multiplication by $\overline{\chi(g)}$, a scalar at each point of $Y$.[^rudin] The kernel of an equivariant map is still decided by the group, as it was there: the equivariant maps $L^2(G/K) \to L^2(G/H)$ correspond to the functions $\kappa$ on $G$ with $\kappa(kgh) = \kappa(g)$ for $k \in K$, $h \in H$, and that is why these three are still called transforms.[^radon]

**Radon transform.** $X$ is the set of points of the plane and $Y$ the set of lines; the group $G$ of rigid motions acts transitively on both, with $K$ the stabilizer of a point and $H$ that of a line. The Radon transform integrates $f$ over each line, and integrating over a line commutes with moving the plane, so it is equivariant; the function $\kappa$ is the incidence relation, $1$ when the point lies on the line. The finite version, with $S_n$ acting on $j$-subsets and $k$-subsets of $\{1, \dots, n\}$ and $\kappa$ the containment relation, is where this description is proved and inverted.[^radon]

**Wavelet transform.** $G$ is the affine group $\{t \mapsto at + b : a > 0\}$, acting on $L^2(\mathbb{R})$ by $(\pi(a,b) f)(t) = a^{-1/2} f((t-b)/a)$, and the transform pairs $f$ with the translates of a chosen window $\psi$:

$$W_\psi f(a, b) = \langle f, \pi(a,b) \psi \rangle, \qquad W_\psi\, \pi(h) = \lambda(h)\, W_\psi \quad (h \in G),$$

where $\lambda$ is translation on functions of $(a,b)$, as in stage one. So $W_\psi$ is an equivariant map from $L^2(\mathbb{R})$ into functions on $G$. What survives of the diagonal is energy: an admissibility condition on $\psi$, $C_\psi = 2\pi\int \lvert \hat\psi(\omega) \rvert^2 \lvert \omega \rvert^{-1} d\omega < \infty$, makes $C_\psi^{-1/2} W_\psi$ an isometry into $L^2$ of the half-plane with the measure $db\,da/a^2$.[^wavelet] Compare stage two, where the transform paired $f$ with the translates $\pi(g) u_\pi$ of the one $K$-fixed vector: here $\psi$ is fixed by no stabilizer at all. Dropping that invariance costs the diagonal, since there is no commutative algebra left to diagonalize, and leaves the isometry, which never depended on characters.

**Gabor transform.** The same construction with a window $g$ translated in time and modulated in frequency, $g_{b,\omega}(t) = g(t-b)\, e^{i\omega t}$: the transform is $\langle f, g_{b,\omega}\rangle$, the kernel in the table is $\overline{g_{b,\omega}}$, and time shifts and modulations of $f$ shift the transform in $(b, \omega)$.[^gabor]

### Children of stage four

| Transform | Domain / symmetry ($G$) | Kernel | Primary application | Parent |
| :--- | :--- | :--- | :--- | :--- |
| **Finite Radon Transform** | $S_n$ acting on $k$-subsets and $j$-subsets of $\{1, \dots, n\}$, $j < k \le n/2$; onto, with an explicit right inverse[^radon] | Incidence: $1$ when the $k$-subset contains the $j$-subset | Spectral analysis of election data: each voter names $k$ of $n$ candidates[^radon] | Radon |
| **[Discrete Wavelet Transform](https://en.wikipedia.org/wiki/Discrete_wavelet_transform)** | The affine group on the lattice $a = a_0^m$, $b = n b_0 a_0^m$, the family asked to be a frame[^finite] | $a_0^{-m/2} \overline{\psi(a_0^{-m} t - n b_0)}$ | JPEG 2000, multiresolution analysis | Wavelet |

## The four canonical forms

Classifying the elements of a matrix group up to conjugacy is the problem of canonical forms, and the four forms of a first course are all the post has used.[^diaconis]

| Normal form | Canonical form of | Where it appears above | Representation theory |
| :--- | :--- | :--- | :--- |
| **[Diagonal](https://en.wikipedia.org/wiki/Spectral_theorem)** | Normal matrices, unitary similarity | Stages one and two | Every irreducible piece appears once |
| **[Frobenius](https://en.wikipedia.org/wiki/Frobenius_normal_form)** | Any matrix over a field $\mathbb{F}$, similarity | The field table: DFT, Hartley, NTT | The cyclic shift is $\mathbb{F}[x]/(x^N-1)$ |
| **[Wedderburn](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem)** | The group algebra $\mathbb{C}[G]$ | Stage three | $L^2(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$ |
| **[Jordan](https://en.wikipedia.org/wiki/Jordan_normal_form)** | Matrices over $\mathbb{C}$, similarity | Where the method fails: a repeated pole of a Laplace transform inverts to $t^k e^{\lambda t}$, a Jordan block, which is [resonance](https://en.wikipedia.org/wiki/Resonance) | Where [complete reducibility](https://en.wikipedia.org/wiki/Maschke%27s_theorem) fails, as for $\mathbb{R}$ acting on the plane by shears |

## Where the thread ends

Two things that carry the name "transform", or are treated alongside them, are outside the four stages, each for a different reason.

**Operators a transform diagonalizes.** The [Hilbert transform](https://en.wikipedia.org/wiki/Hilbert_transform) is convolution with $1/\pi t$ on the line, so it commutes with translation and the Fourier transform diagonalizes it, as multiplication by $-i \mathrm{sgn} \xi$.[^hilbert] The [Stieltjes transform](https://en.wikipedia.org/wiki/Stieltjes_transformation) is the Laplace transform applied twice, $\int_0^\infty f(t)\,dt/(t+x)$; its kernel depends on $t$ and $x$ only through $t/x$, up to the factor $1/x$, so it commutes with dilations and the Mellin transform diagonalizes it, as multiplication by $\pi/\sin \pi p$.[^stieltjes] The [Weyl fractional integral](https://en.wikipedia.org/wiki/Riemann%E2%80%93Liouville_integral) is of the same kind, a Mellin multiplier.[^stieltjes] These are not changes of basis but the kind of operator a change of basis is *for*, and that is why they have no row.

**No basis at all.** Let $A \subset \mathbb Z_N$ have density $\alpha$. The fraction of three-term [arithmetic progressions](https://en.wikipedia.org/wiki/Arithmetic_progression) $x + y = 2z$ with all three terms in $A$ is $\sum_r \hat A(r)^2 \hat A(-2r)$, which is $\alpha^3$, the random share, plus an error of at most $\alpha \max_{r \ne 0} \lvert \hat A(r) \rvert$; so either $A$ has its random share or a character correlates with it, and iterating on the progressions where that character is nearly constant is [Roth's theorem](https://en.wikipedia.org/wiki/Roth%27s_theorem_on_arithmetic_progressions) of 1953.[^roth] The [Gowers norms](https://en.wikipedia.org/wiki/Gowers_norm) (1998) are where this stops. On $\mathbb Z_N$ with $N$ odd the function $e^{2\pi i x^2/N}$ has every Fourier coefficient of modulus $N^{-1/2}$, as flat as Plancherel allows, yet it and three companions have four-term progression count $1$, the largest possible: the transform is blind to the quadratic phases. There are $N^2$ of them against $N$ characters, so they are no basis, and no quadratic transform or inversion formula exists. What survives is the $U^3$ norm, an average over cubes, and an inverse theorem: a function with large $U^3$ norm correlates with a phase built from a two-step [nilpotent group](https://en.wikipedia.org/wiki/Nilpotent_group), a Heisenberg group once more.[^gowers] Nothing is being diagonalized, so the thread does not fray here; it ends.

One idea from a first course in linear algebra reaches across two and a half centuries into number theory, tomography, image compression and quantum computation. Representation theory is what one reaches for where it stops, and it works there because diagonalization was one of its tools and never the whole of it.

## Sources

An AI slop. Brought to you by Anthropic Claude Opus 5.

- Lokenath Debnath and Dambaru Bhatta, *Integral Transforms and Their Applications*, 3rd ed., CRC Press, 2015.
- Audrey Terras, *Fourier Analysis on Finite Groups and Applications*, LMS Student Texts 43, Cambridge, 1999.
- Walter Rudin, *Fourier Analysis on Groups*, Interscience, 1962.
- Elias M. Stein and Guido Weiss, *Introduction to Fourier Analysis on Euclidean Spaces*, Princeton Mathematical Series 32, Princeton, 1971.
- Paul R. Halmos, *Finite-Dimensional Vector Spaces*, 2nd ed., Springer UTM.
- Benjamin Steinberg, *Representation Theory of Finite Groups: An Introductory Approach*, Springer Universitext, 2012.
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Harmonic Analysis on Finite Groups*, Cambridge, 2008 (cited as CST 2008).
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Discrete Harmonic Analysis*, Cambridge, 2018 (CST 2018).
- Persi Diaconis, *Group Representations in Probability and Statistics*, IMS Lecture Notes 11, 1988.
- David A. Levin and Yuval Peres, with Elizabeth L. Wilmer, *Markov Chains and Mixing Times*, 2nd ed., AMS, 2017 (LPW).
- Michael A. Nielsen and Isaac L. Chuang, *Quantum Computation and Quantum Information*, Cambridge.
- George W. Mackey, *Harmonic analysis as the exploitation of symmetry: a historical survey*, Bull. AMS 3 (1980), 543–698.
- Louis Auslander and Richard Tolimieri, *Is computing with the finite Fourier transform pure or applied mathematics?*, Bull. AMS (N.S.) 1 (1979), no. 6, 847–897 (cited as AT).
- W. T. Gowers, *Generalizations of Fourier analysis, and how to apply them*, Bull. AMS (N.S.) 54 (2017), no. 1, 1–44.


[^dates]: Clairaut 1754, Gauss 1805 and Cooley–Tukey 1965: Terras, pp. xv–xvi and 30–31; Cooley–Tukey's own paragraphs are quoted in AT, §II.1, p. 871. Laplace in the 1780s, Fourier 1822: Debnath–Bhatta, §1.1, p. 1.

[^series]: Fourier's memoir of 1807: Terras, p. 30; Mackey, p. 566. The three classical groups $\mathbb{R}$, $\mathbb{T}$, $\mathbb{Z}$, their duals and the three transforms, including $\hat f(e^{i\alpha}) = \sum_n f(n) e^{-in\alpha}$ for $G = \mathbb{Z}$: Rudin, §1.2.7, pp. 12–13; discrete and compact groups are dual: Theorem 1.2.5, p. 9.

[^setting]: Rudin, §1.1 (Haar measure and convolution on a locally compact abelian group). For finite $G$: Steinberg, Definition 4.2.1, whose $L(G)$ is the $L^2(G)$ of this post, with the inner product normalised by $1/\lvert G \rvert$ there and not here; convolution, Definition 5.2.1; the operators commuting with the regular representation are exactly the convolutions, Example 7.3.5, pp. 92–93.

[^hankel]: Debnath–Bhatta, §1.1, p. 5, for Hankel, and Theorem 7.3.4, (7.3.10), for $\mathcal H_n[\nabla^2 f] = -\kappa^2 \tilde f$. Stein–Weiss, Chapter IV, Theorem 1.1, p. 135 (the Fourier transform commutes with orthogonal transformations) and Corollary 1.2 (the transform of a radial function is radial); with Rudin, Theorem 1.2.4(b) (convolution to multiplication), this is the commutativity claimed.

[^legendre]: Terras, p. 180: for $G = O(3)$, $K = O(2)$ the $G$-invariant differential operators are polynomials in the Laplacian on the sphere and the spherical functions are the Legendre polynomials in $\cos\theta$; p. 341 for Laplace and Legendre in the 1780s. Debnath–Bhatta, (14.2.1), for Churchill's 1954 definition $\tilde f(n) = \int_{-1}^{1} P_n(x) f(x)\,dx$ and §14.4 for potential theory. The Hankel formula: Stein–Weiss, Chapter IV, Theorem 3.3, p. 155, for $f(x) = f_0(\lvert x \rvert)$ the transform is $F_0(r) = 2\pi r^{-(n-2)/2}\int_0^\infty f_0(s) J_{(n-2)/2}(2\pi r s) s^{n/2}\,ds$; the other orders, Theorem 3.10, p. 158, $\hat f(x) = F_0(\lvert x \rvert)P(x)$ with $F_0(r) = 2\pi i^{-k} r^{-(n+2k-2)/2}\int_0^\infty f_0(s) J_{(n+2k-2)/2}(2\pi rs) s^{(n+2k)/2}\,ds$.

[^finite]: Debnath–Bhatta: finite Fourier sine and cosine transforms, (10.2.1) and (10.2.4); sine and cosine transforms from the odd and even cases of the Fourier integral, (2.2.8)–(2.2.9) and (2.13.1); finite Laplace transform, (11.2.1); finite Hankel transform, p. 502 and Definition 13.2.1; discrete wavelet transform, (19.3.1) and the frame condition following it.

[^hadamard]: Terras, p. xvi (Hadamard transform = Fourier on $(\mathbb{Z}/2)^n$) and p. 174 (Walsh functions as reordered Hadamard rows). Simon's algorithm as the hidden subgroup problem on $(\mathbb Z_2)^n$: Nielsen–Chuang, Figure 5.5, p. 241.

[^mellin]: Debnath–Bhatta, §8.1, p. 367, for the Riemann–Cahen–Mellin priority and §8.2, (8.2.1)–(8.2.5), for the substitution $x = e^\xi$, $ik = c - p$.

[^frobenius]: Terras, p. 237, for Dedekind's letter and 1897; Mackey, p. 695, for Weyl thirty years later, and pp. 603–604 for the Peter–Weyl theorem of 1927 in the form "one obtains a complete system of orthogonal functions for the group by choosing an orthogonal basis in each subspace" of matrix elements.

[^hilbert]: Debnath–Bhatta, Theorem 9.3.1(f), (9.3.6): $\mathcal{F}[\mathcal{H}f] = (-i \mathrm{sgn} k) \mathcal{F}[f]$.

[^stieltjes]: Debnath–Bhatta, (9.7.1)–(9.7.3), the Stieltjes transform as the Laplace transform of the Laplace transform; (9.8.2), $S\{f(at)\} = \tilde f(az)$; (9.7.11) and Example 9.7.2, the Mellin form with $g(u) = (1+u)^{-1}$, $\mathcal{M}\{\tilde f\}(p) = \tilde f(p)\tilde g(1-p)$ and $\tilde g(1-p) = \pi\,\mathrm{cosec}(\pi p)$. Weyl fractional integral: (5.3.17) and Definition 8.5.1.

[^gegenbauer]: Stein–Weiss, Chapter IV §2: zonal harmonics, p. 143, and Lemma 2.8(c); Theorem 2.12, pp. 146–147, a spherical harmonic of degree $k$ constant on the parallels orthogonal to $e$ is a multiple of the zonal harmonic $Z_e^{(k)}$; Theorem 2.14, p. 149, $Z_{y'}^{(k)}(x') = c_{k,n} P_k^\lambda(x' \cdot y')$ with $\lambda = (n-2)/2$, the Gegenbauer polynomial of p. 148. The Gegenbauer transform: Debnath–Bhatta, (15.5.4), the case $\alpha = \beta = \nu - \tfrac12$ of the Jacobi transform.

[^polynomials]: Jacobi transform: Debnath–Bhatta, (15.2.1), $\int_{-1}^{1} (1-x)^\alpha (1+x)^\beta P_n^{(\alpha,\beta)}(x) F(x)\,dx$, reducing to Legendre at $\alpha = \beta = 0$ (p. 533) and to Gegenbauer at $\alpha = \beta = \nu - \tfrac12$, (15.5.4). Laguerre transform: Debnath–Bhatta, (16.2.1), $\int_0^\infty e^{-x} x^\alpha L_n^\alpha(x) f(x)\,dx$.

[^radon]: Debnath–Bhatta, §1.3, p. 11, for Radon in 1917 and the transform as the integral of $f$ over lines. CST 2008, Exercise 4.2.5, p. 122: for $X = G/K$ and $Y = G/H$, $\mathrm{Hom}_G(L(X), L(Y)) \cong L(K \backslash G / H) = \{f : f(kgh) = f(g)\}$; §6.5, (6.27) and Theorem 6.5.2, p. 189, for $D\colon M^{n-k,k} \to M^{n-j,j}$, $Df(A) = \sum_{B \supset A} f(B)$, $0 \le j < k \le n/2$, and its right inverse; §6.4, pp. 184–185, for the election data.

[^wavelet]: Debnath–Bhatta, §1.3, pp. 9–12, for Gabor (1946) and Morlet–Grossmann (1982–84); Definition 19.2.1, (19.2.1), for admissibility and Theorem 19.2.2, (19.2.8)–(19.2.9), for $\int\!\!\int W_\psi f\, \overline{W_\psi g}\; db\,da/a^2 = C_\psi \langle f, g \rangle$ with $C_\psi = 2\pi\int \lvert\hat\psi(\omega)\rvert^2 \lvert\omega\rvert^{-1} d\omega$. Equivariance is the identity $W_\psi(\pi(h)f)(g) = \langle f, \pi(h^{-1}g)\psi\rangle$ for unitary $\pi$. The comparison with the spherical function $\langle u_\pi, \pi(g)u_\pi\rangle$ (CST 2008, Cor. 4.6.4) is done by Calude Opus 5.

[^gabor]: Debnath–Bhatta, §1.3, pp. 9–10, (1.3.1): $G[f](t,\omega) = \int f(\tau)\overline{g(\tau - t)}e^{-i\omega\tau}d\tau = \langle f, g_{t,\omega}\rangle$ with $g_{t,\omega}(\tau) = g(\tau - t)e^{i\omega\tau}$, "obtained by translating and modulating a function $g$"; the discrete family $g_{m,n}$ is called there the Weyl–Heisenberg coherent states.

[^hsp]: Nielsen–Chuang, p. 221 (the amplitudes of a state cannot be read out, so the quantum Fourier transform is not a fast FFT: its output is read as a measurement of which irreducible representation the state lies in) and §5.4.3 with Figure 5.5, pp. 240–241 (the hidden subgroup problem; Simon's problem on $(\{0,1\}^n, \oplus)$, period and order finding on $(\mathbb{Z}, +)$).

[^halmos]: Halmos, §79–80 (spectral theorem, self-adjoint and then normal), §84 Exercise 6 (a commutative set of normal transformations can be simultaneously diagonalized), §81 (complex proper values of an orthogonal transformation come in conjugate pairs, giving plane rotations).

[^mackey]: Mackey, §2 (pp. 547–548) for translation becoming multiplication, §9 (pp. 568–575) for differentiation becoming multiplication, the potential and heat-kernel formulas, first obtained by other means (pp. 570–571), and p. 574 for the sphere: "this surface $S$ cannot be made into a group at all in a manner consistent with its topology", and $SO(3)$ "has no invariant one-dimensional subspace of measurable functions except for the space of constants".

[^rudin]: Rudin, p. 9: $\hat f(\gamma) = \int_G f(x)(-x,\gamma)\,dx$ and, by Theorem 1.2.2, $\hat f$ is the Gelfand transform of $f$; Theorem 1.2.4(b), $\widehat{f \ast g} = \hat f \hat g$, (c), translation by $x$ multiplies $\hat f$ by $(-x,\gamma)$, and (e), $f \ast \gamma = \hat f(\gamma)\gamma$; §1.6, the Plancherel theorem; §1.7, the Pontryagin duality theorem. For finite abelian groups, Steinberg, Definition 5.3.4 and Lemma 5.4.9.

[^laplace]: Debnath–Bhatta, §1.1, p. 2 (the Laplace transform is a special case of the Fourier transform for functions on the positive axis, easier because the kernel decays and the result is analytic in $s$); §3.2, (3.2.1)–(3.2.6), the Laplace transform and its inverse derived from the Fourier integral of $e^{-cx}f(x)H(x)$. Non-orthogonality on the real axis: $\int_0^\infty e^{-s_1 t}e^{-s_2 t}\,dt = 1/(s_1 + s_2) \ne 0$. Mackey, pp. 550–551 (Laplace's generating functions of 1782, $t^n$ as characters of $\mathbb{Z}$, the difference equation becoming algebraic).

[^dct]: CST 2008, Appendix 1, pp. 392–399: the sixteen DCT/DST bases as eigenvectors of path-graph operators obtained by folding under an involution; the DCT-2 from the involution $k \mapsto 2n-1-k$ on $C_{2n}$, in the paragraph headed "DCT-2", p. 398.

[^dftspectrum]: Debnath–Bhatta, Appendix A-6, (A-6.11)–(A-6.13), for the Hermite functions as an orthogonal basis of $L^2(\mathbb{R})$ with $\mathcal{F}h_n = (-i)^n h_n$; the Hermite transform, (17.2.1), is $\int e^{-x^2} H_n(x) F(x)\,dx$, the expansion of $e^{-x^2/2}F$ in the $h_n$. For the DFT: CST 2018, Proposition 4.1.2 ($F^4 = I$) and Theorem 4.3.1 with Table 4.1 (multiplicities $m+1, m, m, m-1$ for $N = 4m$); AT, Theorem 1.1.2, p. 855, for the trace as a Gauss sum.

[^gelfandpair]: CST 2008, Definition 4.3.1 (Gelfand pair: $L(K \backslash G/K)$ commutative under convolution), Theorem 4.4.2, p. 125 (equivalently $\mathrm{Hom}_G(L(X), L(X))$ commutative, equivalently $L(X)$ multiplicity-free), Theorem 4.6.2, p. 133 (equivalently $\dim V^K \le 1$ for every irreducible $V$), Corollary 4.6.4, p. 134 ($\phi(g) = \langle u, \rho(g)u \rangle$ is the spherical function, and $v \mapsto \langle v, \rho(g)u\rangle$ is an isometric immersion of $V$ into $L(X)$ up to the factor $\sqrt{\dim V/\lvert X \rvert}$, which with Schur's lemma gives the projection statement), Lemma 4.5.4, p. 129 (spherical functions are the multiplicative linear functionals of $L(K\backslash G/K)$), and §4.7, p. 135 ($\mathcal{F}f(i) = \langle f, \phi_i \rangle$ for $K$-invariant $f$). Steinberg, Definition 7.3.4 and Example 7.3.5, pp. 92–93, for $(G,\{1\})$.

[^wedderburn]: Steinberg, Definition 5.5.2, $\hat f(\pi)_{ij} = \sum_g f(g)\overline{\pi_{ij}(g)}$, and Theorem 5.5.6, p. 66 (the Fourier transform $L(G) \to M_{d_1}(\mathbb{C}) \times \cdots \times M_{d_s}(\mathbb{C})$ is a ring isomorphism); Corollary 4.4.5 ($\lvert G \rvert = \sum d_i^2$) and Theorem 4.4.6 (the $\sqrt{d_k}\,\pi^{(k)}_{ij}$ are an orthonormal basis of $L(G)$), pp. 44–45. Diaconis, p. 7, and CST 2018, (10.78), define the transform without the conjugate; the two conventions differ by replacing $\pi$ with its conjugate representation and nothing below depends on the choice. CST 2008, Lemma 9.5.3 and Theorem 9.5.4, pp. 286–287, for $(G \times G, \Delta G)$: $L(G) = \bigoplus_\sigma M^\sigma$ with $M^\sigma \cong \sigma' \otimes \sigma$, multiplicity-free, spherical function $\chi_\sigma/d_\sigma$.

[^diaconis]: Diaconis, p. 21, $\lVert P - Q \rVert = \max_{A \subset G} \lvert P(A) - Q(A) \rvert$; Chapter 3B Lemma 1, p. 24 (upper bound lemma); 3C Theorem 2, p. 25 ($\mathbb Z_p$: "somewhat more than $p^2$ steps are required"); 3D Theorem 5, p. 36 (random transpositions: for $k = \frac12 n\log n + cn$, $\lVert P^{\ast k} - U \rVert \le ae^{-2c}$ if $c > 0$ and $\ge \frac1e - e^{-e^{-2c}} + o(1)$ if $c < 0$); p. 14, "for matrix groups, the classification of matrices up to conjugacy is the problem of canonical forms", and Proposition 6 there, $\hat f(\rho) = \lambda I$ with $\lambda = \frac{1}{d_\rho}\sum f(t)\chi_\rho(t)$ for a class function $f$. The name cutoff and the mixing time $(\frac12 + o(1))n\log n$: LPW, §8.2, p. 102, and Chapter 18, §18.1, for the definition. Cayley graphs: Steinberg, Theorem 5.4.10 (abelian) and Exercise 5.12 (class functions); the block statement is Theorem 5.5.6 read on $L(G)$.

[^fft]: CST 2018, §10.7, pp. 397–398, and Exercise 10.7.3 (Diaconis–Rockmore's algorithm for $K \le G$, with Cooley–Tukey as the case $G = \mathbb{Z}_{nm}$, $K = \mathbb Z_m$, and its recursive form along a chain of subgroups); §5.4 for Rader, and AT, §III.2, pp. 882–883.

[^roth]: Gowers, §3, pp. 4–6: Roth 1953 (his reference [45]), the identity, the bound $\alpha\max_{r \ne 0}\lvert\hat A(r)\rvert$, Lemma 3.2 and the iteration.

[^gowers]: Gowers, §7, p. 17 (the example $\omega^{x^2}, \omega^{-3x^2}, \omega^{3x^2}, \omega^{-x^2}$, expectation $1$, $\lvert\hat f(r)\rvert = n^{-1/2}$ for $n$ odd), §8, p. 18 ($n^2$ quadratic phase functions, no basis; the $U^3$ norm as an average over cubes), §11.1, p. 28 (no transform), Theorem 11.2 and pp. 25–27 (inverse theorem, nilsequences, the Heisenberg group); the 1998 paper is his reference [17].
