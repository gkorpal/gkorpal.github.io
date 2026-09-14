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

From Laplace in the 1780s to Gowers norms in the 1990s, the whole zoo is one idea repeated, and the idea is a piece of linear algebra from a first course. What follows is a map: how far that one piece reaches, where it gives out, and what takes over.

## The transforms in chronological order

| Year | Transform | Domain / Group ($G$) | Kernel | Primary application |
| :--- | :--- | :--- | :--- | :--- |
| **1754** | **[Discrete Fourier Transform (DFT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)** | Cyclic group $(\mathbb{Z}_N, +)$ | $e^{-2\pi i jk/N}$ | Orbit determination, and thereafter the whole of digital signal processing[^dates] |
| **1782** | **[Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform)** | $([0,\infty), +)$, continued to $\Re s > 0$ | $e^{-st}$ | Control theory, ODE stability, circuit analysis[^dates] |
| **1782** | **[Spherical Harmonic Transform](https://en.wikipedia.org/wiki/Spherical_harmonics)** | 2-sphere $S^2 = SO(3)/SO(2)$ | $\overline{Y_\ell^m(\theta,\varphi)}$ | Geopotential models, atomic orbitals, CMB analysis |
| **1805** | **[Fast Fourier Transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform)** | Cyclic group $(\mathbb{Z}_N, +)$ | the DFT kernel, rearranged | Telecom, spectral analysis, fast convolution[^dates] |
| **1822** | **[Continuous Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)** | Real line $(\mathbb{R}, +)$ | $e^{-i\omega t}$ | Heat conduction, wave mechanics, quantum theory[^dates] |
| **1875** | **[Hankel Transform](https://en.wikipedia.org/wiki/Hankel_transform)** | Radial functions on $\mathbb{R}^n$, a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) | $t J_\nu(ut)$ | Axisymmetric boundary value problems, optics, acoustics[^hankel] |
| **1893** | **[Walsh-Hadamard Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | Hypercube $(\mathbb{Z}_2)^n$ | $(-1)^{\langle x, y \rangle}$ | Error correcting codes, Mariner Mars telemetry, Simon's algorithm[^hadamard] |
| **1896** | **[Mellin Transform](https://en.wikipedia.org/wiki/Mellin_transform)** | Multiplicative reals $(\mathbb{R}^+, \times)$ | $t^{s-1}$ | Analytic number theory, Dirichlet series, asymptotics[^mellin] |
| **1897** | **[Fourier Transform on Finite Groups](https://en.wikipedia.org/wiki/Fourier_transform_on_finite_groups)** | Finite groups: [$S_n$](https://en.wikipedia.org/wiki/Symmetric_group), $D_n$, $GL_2(\mathbb F_q)$ | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Representation theory, card shuffling, spectral graph theory[^frobenius] |
| **1905** | **[Hilbert Transform](https://en.wikipedia.org/wiki/Hilbert_transform)** | Real line $(\mathbb{R}, +)$ | $1/\pi(t-u)$, p.v. | Analytic signals, envelope detection, aerofoil theory[^hilbert] |
| **1917** | **[Radon Transform](https://en.wikipedia.org/wiki/Radon_transform)** | Lines in $\mathbb{R}^2$, affine hyperplanes in $\mathbb{R}^n$ | $\delta(u - \langle x, \theta \rangle)$ | CT and PET tomography, seismic imaging[^radon] |
| **1927** | **[Peter-Weyl Transform](https://en.wikipedia.org/wiki/Peter%E2%80%93Weyl_theorem)** | [Compact Lie groups](https://en.wikipedia.org/wiki/Compact_group) $SO(3)$, $SU(2)$ | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Angular momentum, particle physics, molecular replacement |
| **1942** | **[Hartley Transform](https://en.wikipedia.org/wiki/Hartley_transform)** | Real line $(\mathbb{R}, +)$ | $\cos ut + \sin ut$ | Real valued signal processing without complex arithmetic |
| **1946** | **[Gabor Transform / STFT](https://en.wikipedia.org/wiki/Short-time_Fourier_transform)** | Time-frequency plane, the [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) | $\overline{g(t-b)} e^{-i\omega t}$ | Spectrograms, speech, time-frequency analysis[^wavelet] |
| **1947** | **[Z-Transform](https://en.wikipedia.org/wiki/Z-transform)** | $(\mathbb{Z}, +)$, continued off the unit circle | $z^{-n}$ | Digital filter design (IIR and FIR), sampled-data control |
| **1969** | **[Chirp Z-Transform (CZT)](https://en.wikipedia.org/wiki/Chirp_Z-transform)** | Spiral contours in $\mathbb{C}$ | $A^{-n}W^{nk}$ | Zoom spectrum analysis, radar |
| **1971** | **[Number-Theoretic Transform (NTT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_(general)#Number-theoretic_transform)** | $(\mathbb{Z}_N,+)$ with $\omega$ a [root of unity](https://en.wikipedia.org/wiki/Root_of_unity) in $\mathbb{F}_q^\times$ | $\omega^{jk} \bmod q$ | Exact integer convolution, lattice post-quantum cryptography |
| **1974** | **[Discrete Cosine Transform (DCT)](https://en.wikipedia.org/wiki/Discrete_cosine_transform)** | $\mathbb{Z}_{2N}$, restricted to even extensions | $\cos\frac{\pi k(2n+1)}{2N}$ | JPEG, MPEG, MP3, plausibly the most executed transform ever written[^dct] |
| **1980** | **[Fractional Fourier Transform (FrFT)](https://en.wikipedia.org/wiki/Fractional_Fourier_transform)** | Phase space rotations $SO(2)$ | chirp, $e^{i\pi[(t^2+u^2)\cot\alpha - 2tu\csc\alpha]}$ | Chirped optical signals, radar filtering |
| **1984** | **[Wavelet Transform](https://en.wikipedia.org/wiki/Continuous_wavelet_transform)** | The [affine](https://en.wikipedia.org/wiki/Affine_group), or "$ax+b$", group | $a^{-1/2} \overline{\psi((t-b)/a)}$ | JPEG 2000, denoising, LIGO analysis[^wavelet] |
| **1994** | **[Quantum Fourier Transform (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform)** | Cyclic group $(\mathbb{Z}_{2^n}, +)$ | $e^{2\pi i jk/2^n}$ | Shor's factoring algorithm[^qft] |
| **1998** | **[Higher-Order Fourier Analysis](https://en.wikipedia.org/wiki/Gowers_norm)** | $\mathbb{Z}_N$ or $\mathbb{F}_p^n$, with polynomial phases | none: the $U^k$ norms and an inverse theorem | Additive combinatorics, the Green-Tao theorem |

Two and a half centuries, a dozen fields, and no obvious reason why any of these should be thought of together. The sections below take the table in the order in which the one idea behind it is stretched: where it holds outright, where it holds on a space that is not quite a group, where it has to be replaced by something larger, and what all of it is for.

## What a transform does

The idea is diagonalization. Two matrices $A$ and $B$ are similar, $A = P^{-1} B P$, when they are the same operator written in two bases, and a [canonical form](https://en.wikipedia.org/wiki/Canonical_form#Linear_algebra) is a distinguished representative of each such class; for similarity it is the [Jordan form](https://en.wikipedia.org/wiki/Jordan_normal_form). Now require the change of basis to be unitary, $A \mapsto U A U^{*}$, and restrict to [normal](https://en.wikipedia.org/wiki/Normal_matrix) operators. The canonical form becomes the diagonal one, and that statement is the [spectral theorem](https://en.wikipedia.org/wiki/Spectral_theorem).[^halmos] Here is the whole post in one sentence.

> An integral transform **is** the $U$.

Literally. Let $\tau_a$ be translation by $a$ on the real line and $\mathcal{F}$ the Fourier transform. Then

$$\mathcal{F} \tau_a \mathcal{F}^{-1} = \text{multiplication by } e^{-i a \xi}$$

A multiplication operator rescales its input point by point, exactly as a diagonal matrix rescales each coordinate. So the Fourier transform is the $U$ that makes translation diagonal, and since differentiation is infinitesimal translation, it makes differentiation diagonal too, as multiplication by $i\xi$. A differential equation with constant coefficients thereby becomes an algebraic one, and a large part of what the Fourier transform is used for comes down to that.[^mackey]

Why does one $U$ serve several operators? Because normal operators that commute with one another can be diagonalized **simultaneously**, in one common eigenbasis, and differentiation, translation and convolution all commute.[^halmos] The **Hilbert transform** is the clean example: it is convolution with $1/\pi t$, so it commutes with translation, so the same $U$ diagonalizes it, and in the Fourier basis it is multiplication by $-i \mathrm{sgn} \xi$.[^hilbert] Its row in the table is not another change of basis but the kind of operator a change of basis is *for*.

One caveat. Diagonalizing means finding eigenvectors, and translation on $\mathbb{R}$ has none in $L^2$: the functions $e^{i\xi t}$ have constant modulus and are not square-integrable. There the "diagonal" is the [multiplication-operator form](https://en.wikipedia.org/wiki/Spectral_theorem#Multiplication_operator_version) of the spectral theorem. On a finite group of order $N$, by contrast, $L^2(G)$ is $\mathbb{C}^N$, the transform is an $N \times N$ unitary matrix, and the first course applies verbatim. The finite case is the one this post leans on.

## The intact case: abelian groups

> A transform diagonalizes exactly those operators which **commute with the symmetry of the domain**.

If the domain carries a group action, the operators commuting with it are the [convolution](https://en.wikipedia.org/wiki/Convolution) operators, and when $G$ is abelian they commute with each other, so they share one eigenbasis. That eigenbasis is the set of [characters](https://en.wikipedia.org/wiki/Character_group) of $G$, the functions with $\chi(xy) = \chi(x)\chi(y)$: convolving a character with anything returns a multiple of the same character, the multiple being the Fourier coefficient. So the group decides the kernel $K(t,u)$ of the table, which is just the characters written out; nothing is chosen.

One hypothesis, that $G$ is a [locally compact abelian group](https://en.wikipedia.org/wiki/Locally_compact_abelian_group), supplies everything else: the [dual group](https://en.wikipedia.org/wiki/Pontryagin_duality#The_dual_group) $\hat G$ of characters, the [convolution theorem](https://en.wikipedia.org/wiki/Convolution_theorem), and the [Plancherel](https://en.wikipedia.org/wiki/Plancherel_theorem) isometry. One theorem packages them: $L^1(G)$ under convolution is a commutative Banach algebra, its multiplicative functionals are exactly the characters, and the Fourier transform is its [Gelfand transform](https://en.wikipedia.org/wiki/Gelfand_representation).[^rudin]

Call this the **intact case**. It covers ten rows of the table.

- The **DFT** and its fast evaluation, the **FFT**.
- The **continuous Fourier transform**.
- The **Mellin transform**, which is the Fourier transform on $(\mathbb{R}^+, \times)$: substitute $x = e^{\xi}$.[^mellin]
- The **Walsh–Hadamard transform**, which is the Fourier transform on $(\mathbb{Z}_2)^n$ under an engineer's name.[^hadamard]
- The **DCT**, which is the DFT on $2N$ points restricted to the functions even under the reflection $n \mapsto -1-n$; the other reflections of the cycle and of the path give the other fifteen cosine and sine transforms.[^dct]
- The **QFT**, which is the DFT on $\mathbb{Z}_{2^n}$ built as a quantum circuit.
- The **NTT** and the **Hartley transform**, which keep the group and change the field; the next paragraph explains them.
- The **fractional Fourier transform**, which is a power of the Fourier transform rather than a new kernel: the Hermite functions $h_n$ are an eigenbasis of $\mathcal{F}$ on $L^2(\mathbb{R})$, with $\mathcal F h_n = (-i)^n h_n$, and $\mathcal F_\alpha$ puts $e^{-in\alpha}$ on $h_n$; summed over $n$, that is the chirp of the table.[^dftspectrum]

The field variants are settled by one more canonical form. The [Frobenius normal form](https://en.wikipedia.org/wiki/Frobenius_normal_form) decomposes a matrix over any field into [companion](https://en.wikipedia.org/wiki/Companion_matrix) blocks; the cyclic shift on $\mathbb{Z}_N$ is the companion matrix of $x^N - 1$, the [circulant matrices](https://en.wikipedia.org/wiki/Circulant_matrix) are $K[x]/(x^N-1)$, and the transform is decided by how $x^N - 1$ factors.

| Field $K$ | How $x^N - 1$ factors | Best canonical form | Transform |
| :--- | :--- | :--- | :--- |
| $\mathbb{C}$ | into $N$ distinct linear factors | Diagonal | **DFT** |
| $\mathbb{R}$ | into $x \pm 1$ and quadratics $x^2 - 2\cos(2\pi k/N) x + 1$ | $2 \times 2$ rotation blocks | **Hartley** |
| $\mathbb{F}_q$ | into distinct linear factors exactly when $N \mid q-1$ | Diagonal over $\mathbb{F}_q$ | **NTT** |

The middle row is the real spectral theorem: no real basis separates a conjugate pair of eigenvalues, so the Hartley kernel $\cos\nu x + \sin\nu x$ pairs $\nu$ with $-\nu$ and no real transform can do better.[^halmos] The last row says a change of field need cost nothing, provided $\mathbb{F}_q^\times$ contains an $N$th root of unity.

## One step out: homogeneous spaces

The **Hankel transform** acts on radial functions and the **spherical harmonic transform** on the sphere. Neither domain is a group: the sphere cannot be made one, and $SO(3)$, which acts on it, has no invariant one-dimensional space of functions but the constants.[^mackey] So there are no characters. Yet both transforms are diagonal: the Hankel transform turns the radial Laplacian into multiplication by $-\kappa^2$,[^hankel] and spherical harmonics are eigenfunctions of the Laplacian on the sphere.

What suffices is less than a commutative group. Write the domain as $X = G/K$, a group modulo the stabilizer $K$ of a point: $S^2 = SO(3)/SO(2)$, and radial functions are the $SO(n)$-invariant functions on $\mathbb{R}^n$. The operators on functions on $X$ that commute with $G$ form an algebra, and $(G, K)$ is called a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) when that algebra is commutative. Then three things hold at once: the operators diagonalize simultaneously, as in the abelian case; the functions on $X$ split into pieces on which $G$ acts irreducibly, with no piece repeated; and each piece $V$ contains, up to scale, one function fixed by $K$. Call it $u$, and write $\rho(g)$ for the action of $g$ on $V$. The [spherical function](https://en.wikipedia.org/wiki/Zonal_spherical_function) of the piece is $\phi(g) = \langle u, \rho(g)u\rangle$, and it is the multiplicative functional of the commutative algebra exactly as a character is for $L^1(G)$.[^gelfandpair] The spherical functions are the kernel, Legendre polynomials on the sphere and Bessel functions for radial functions, and the transform of $f$ is its inner products with the translates $\rho(g)u$.

The abelian case is not a separate theory. With $K = \{1\}$, $(G, \{1\})$ is a Gelfand pair if and only if $G$ is abelian.[^gelfandpair] The real hypothesis was never commutativity of $G$ but commutativity of the operators that commute with $G$, equivalently no repeated piece. This is the first place the transforms need representation theory, and for one job: to say when a transform is still diagonal.

## Two steps out: non-abelian groups

The **Fourier transform on a finite group** and the **Peter–Weyl transform** act on functions on a non-commutative $G$, and now the convolution operators do not commute with each other, so no single eigenbasis exists. What replaces a character is a [representation](https://en.wikipedia.org/wiki/Group_representation): a family of $d_\pi \times d_\pi$ matrices $\pi(g)$, acting on a space $V_\pi$, that multiply as the group does. It is [irreducible](https://en.wikipedia.org/wiki/Irreducible_representation) when $V_\pi$ has no invariant subspace, and a character is the case $d_\pi = 1$. The transform of $f$ at $\pi$ is the matrix $\hat f(\pi) = \sum_g f(g)\pi(g)$, and convolution becomes matrix multiplication, block by block. That this is a ring isomorphism $L(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$ is [Wedderburn's theorem](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem), the abelian case being the one where every block is $1 \times 1$.[^wedderburn] On its face this is a defeat: block-diagonal is not diagonal.

One observation rescues it. Let $G \times G$ act on functions on $G$ by translating on both sides, $f(g) \mapsto f(g_1^{-1} g g_2)$. Under that larger action the decomposition $L(G) = \bigoplus_\pi V_\pi \otimes V_\pi^{*}$ has no repeated piece, so $G \times G$ with its diagonal subgroup $\Delta G = \{(g, g)\}$ is a Gelfand pair, and its spherical functions are $\chi_\pi / d_\pi$, where $\chi_\pi(g) = \mathrm{tr} \pi(g)$ is what "character" means for a non-abelian group.[^wedderburn] So the non-abelian transform is a diagonalization after all, of the two-sided action; the $d_\pi \times d_\pi$ blocks are what the one-sided action alone can see. The history ran the same way: Frobenius invented representation theory in 1897 to answer a question of Dedekind's about group determinants, and it took until Weyl, thirty years later, for anyone to see that he had extended Fourier analysis from commutative to non-commutative groups.[^frobenius]

Two payoffs the table names. A [Cayley graph](https://en.wikipedia.org/wiki/Cayley_graph) on $G$ has adjacency matrix equal to convolution by the indicator of its generating set $S$, so its eigenvalues are those of the blocks $\hat 1_S(\pi)$, each repeated $d_\pi$ times; when $G$ is abelian, or $S$ is a union of conjugacy classes, the blocks are scalars and the eigenvalues are the character sums $\frac{1}{d_\pi}\sum_{s \in S} \chi_\pi(s)$ themselves.[^diaconis] And a shuffle is a probability $P$ on $S_n$, $k$ shuffles is $P^{*k}$, so $\widehat{P^{*k}} = \hat P^k$ and Plancherel bounds the distance from the uniform distribution $U$ by a sum over representations:

$$\lVert P^{*k} - U \rVert^2 \le \frac14 \sum_{\pi \neq 1} d_\pi \mathrm{Tr}\big(\hat P(\pi)^k \hat P(\pi)^{*k}\big)$$

Put $\mathbb{Z}_p$ into it, stepping by $\pm 1$, and somewhat more than $p^2$ steps are needed; put $S_n$ in, swapping a random pair each step, and $\frac12 n\log n$ shuffles suffice, the distance staying near $1$ until then and collapsing after, which is the [cutoff phenomenon](https://en.wikipedia.org/wiki/Cutoff_phenomenon).[^diaconis]

This is also where the canonical forms of the first course meet the groups: classifying the elements of a matrix group up to conjugacy is the problem of canonical forms, and the four forms below are all the table ever uses.[^diaconis]

| Normal form | Canonical form of | Transform | Representation theory |
| :--- | :--- | :--- | :--- |
| **[Diagonal](https://en.wikipedia.org/wiki/Spectral_theorem)** | Normal matrices, unitary similarity | The intact case and the Gelfand pairs | Every irreducible piece appears once |
| **[Frobenius](https://en.wikipedia.org/wiki/Frobenius_normal_form)** | Any matrix over a field, similarity | DFT, Hartley, NTT | The cyclic shift is $K[x]/(x^N-1)$ |
| **[Wedderburn](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem)** | The group algebra $\mathbb{C}[G]$ | Fourier on a finite group, Peter–Weyl | $L(G) \cong \bigoplus_\pi M_{d_\pi}(\mathbb{C})$ |
| **[Jordan](https://en.wikipedia.org/wiki/Jordan_normal_form)** | Matrices over $\mathbb{C}$, similarity | Where the method fails: a repeated pole inverts to $t^k e^{\lambda t}$, a Jordan block, which is [resonance](https://en.wikipedia.org/wiki/Resonance) | Where [complete reducibility](https://en.wikipedia.org/wiki/Maschke%27s_theorem) fails, as for $\mathbb{R}$ acting on the plane by shears |

## Off the axis and off the diagonal

Six rows remain, stretched in three directions.

**Laplace, $Z$, chirp $Z$: characters off the unitary axis.** $e^{-st}$ with $\Re s > 0$ is a character of $(\mathbb{R}, +)$ continued off the imaginary axis, which is why it decays. The **Laplace transform** is the Fourier transform on the half-line with that continuation built in, easier to handle because the kernel decays and the result is analytic in $s$, and it pays for that with orthogonality: the kernels $e^{-st}$ for real $s$ are not orthogonal, so there is no Plancherel formula on the real axis of $s$, and the isometry is recovered only line by line, on $\Re s = c$, where the Laplace transform of $f$ is the Fourier transform of $e^{-ct}f$.[^laplace] The **$Z$-transform** makes the same bargain on $\mathbb{Z}$; the **chirp $Z$-transform** evaluates it along a spiral.

**Radon: an [intertwiner](https://en.wikipedia.org/wiki/Equivariant_map), not a change of basis.** The **Radon transform** carries functions on points to functions on lines, and the rigid motions act on both; it intertwines two representations of one group. There is a finite model in which everything is exact. Let $S_n$ act on the $k$-subsets and the $j$-subsets of $\{1, \dots, n\}$, $j < k \le n/2$, and let $D$ send a function on $k$-subsets to the function on $j$-subsets obtained by summing over the $k$-subsets containing each one. That is a Radon transform; it is onto, with an explicit right inverse, and there are more $k$-subsets than $j$-subsets, so nothing better is possible. In general the intertwiners from $L(G/K)$ to $L(G/H)$ are the functions on $G$ invariant under $K$ on the left and $H$ on the right, so a Radon transform is an incidence relation read as such a function.[^radon]

**Wavelets and Gabor: the coefficients without the diagonal.** The **wavelet** and **Gabor** transforms keep a group, the affine and Heisenberg groups, but give up diagonalization altogether. What survives is energy: an [admissibility](https://en.wikipedia.org/wiki/Continuous_wavelet_transform) condition makes the family of shifted, scaled copies resolve the identity.[^wavelet] Compare the Gelfand pair, where the transform paired $f$ with the translates $\rho(g)u$ of the one $K$-fixed vector: a wavelet transform pairs $f$ with the translates $\pi(g)\psi$ of a chosen window $\psi$, and $\psi$ is fixed by no stabilizer at all. Dropping that invariance costs the diagonal, since there is no commutative algebra left to diagonalize, and leaves the isometry, which never depended on characters.

## What transforms are for

**To multiply instead of convolve.** A filter is a convolution and becomes a multiplier. A differential equation with constant coefficients becomes algebraic, and its solution comes back as a convolution of the data with a fixed kernel; the Coulomb potential of a charge distribution and the heat kernel are two such formulas, both first obtained without the Fourier transform that explains them.[^mackey] Random walks on groups and Dirichlet series are the same fact on $S_n$ and on $(\mathbb{R}^+, \times)$.

**To go fast.** The DFT and FFT are one transform; the speed comes from the group. For even $N$ the even points of $\mathbb{Z}_N$ are a subgroup of index two, and splitting the sum along it turns one transform of length $N$ into two of length $N/2$; repeated, that is [Cooley–Tukey](https://en.wikipedia.org/wiki/Cooley%E2%80%93Tukey_FFT_algorithm) and $N^2$ becomes $N \log N$. Sines and cosines never enter, only a subgroup to split along, so the same manoeuvre gives fast transforms on $(\mathbb{Z}_2)^n$ and, with bases adapted to a chain of subgroups, on any finite group.[^fft] For prime $N$ there is no subgroup, and [Rader](https://en.wikipedia.org/wiki/Rader%27s_FFT_algorithm) instead uses the cyclic group $\mathbb{F}_p^\times$ to rewrite the transform as a convolution of length $p-1$.[^fft] Gauss had the composite case in 1805, for the orbit of Juno; the rediscovery of 1965 is the moment the hardware made it worth having.[^dates]

**To measure.** The **quantum Fourier transform** uses about $n^2$ gates on $N = 2^n$ points where the FFT uses $n2^n$. That sounds like news for signal processing and is not: the amplitudes of a quantum state cannot be read out, and the input state cannot in general be prepared.[^qft] What a quantum computer gets from a transform is a **measurement**. An orthogonal decomposition of a Hilbert space *is* a projective measurement, the Wedderburn decomposition is such a decomposition, and applying the Fourier transform and reading the result is the measurement of which representation one is in, the *character measurement*.[^hsp] Nearly every exponential quantum speed-up applies it to the [hidden subgroup problem](https://en.wikipedia.org/wiki/Hidden_subgroup_problem): given a function on $G$ that is constant on the cosets of an unknown subgroup $H$ and distinct between them, find $H$. Querying the function leaves a state spread over one coset of $H$; the character measurement then reports a representation, and for abelian $G$ that is a character trivial on $H$, which pins $H$ down in time polynomial in $\log\lvert G\rvert$. [Simon's algorithm](https://en.wikipedia.org/wiki/Simon%27s_problem) is the case $(\mathbb{Z}_2)^n$ on the Walsh–Hadamard transform and [Shor's](https://en.wikipedia.org/wiki/Shor%27s_algorithm) the case $\mathbb{Z}$ on the QFT.[^hsp]

**To count.** Let $A \subset \mathbb Z_N$ have density $\alpha$ and write $A$ for its indicator. A three-term [arithmetic progression](https://en.wikipedia.org/wiki/Arithmetic_progression) is a solution of $x + y = 2z$, so the fraction of solutions lying in $A$ is $\langle A * A, A(\cdot/2)\rangle$, a convolution paired with a dilation, and the convolution theorem turns it into $\sum_r \hat A(r)^2 \hat A(-2r)$. The $r = 0$ term is $\alpha^3$, the fraction a random set of the same density would have, and the rest is at most $\alpha \max_{r \ne 0} \lvert \hat A(r) \rvert$. So either $A$ has its random share of progressions or one character correlates with it, and a character is nearly constant on long progressions, on one of which $A$ is then denser; iterating is [Roth's theorem](https://en.wikipedia.org/wiki/Roth%27s_theorem_on_arithmetic_progressions) of 1953.[^roth] The transform counts solutions of linear equations, and the size of the largest coefficient measures how random a set is.

## Why the kernel is forced

The intact case said the group decides the kernel because the characters are the only common eigenbasis. There is a stronger sense in which the DFT is forced, and it closes the circle. On functions on $\mathbb{Z}/n$, with $\chi(k) = e^{2\pi i k/n}$, let $T_x$ be translation by $x$ and $M_y$ multiplication by the character $\chi(-y \cdot)$. They do not commute, $T_x M_y = \chi(xy) M_y T_x$, and together with the scalars $\chi(z)$ they generate the finite [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group); the map $(x, y, z) \mapsto \chi(z) M_y T_x$ is an irreducible representation of it. An automorphism $J$ of that group exchanges the roles of $x$ and $y$, which gives a second realization of the same irreducible representation, and by [Schur's lemma](https://en.wikipedia.org/wiki/Schur%27s_lemma) the operator carrying one realization to the other is unique up to a scalar. That operator is the Fourier transform: $\mathcal{F} T_x = M_x \mathcal{F}$ and $\mathcal{F} M_y = T_{-y}\mathcal{F}$.[^heisenberg] So the DFT is the one unitary, up to a phase, that exchanges translation with modulation, and the group leaves no room for choice. And since $J$ has order four, so does $\mathcal{F}$: that is the $F^4 = I$ the fractional Fourier transform was built on.

The order-four fact is also where the continuous and discrete cases part company. $\mathcal{F}^2$ is the reflection $f(x) \mapsto f(-x)$, so the eigenvalues of $\mathcal{F}$ are among $\pm 1, \pm i$, and a fractional power $\mathcal F_\alpha = \mathcal{F}^{2\alpha/\pi}$ needs a basis inside each eigenspace. On $L^2(\mathbb{R})$ the eigenspaces are infinite-dimensional, and the oscillator $-d^2/dx^2 + x^2$, which commutes with $\mathcal{F}$, picks the Hermite functions out of them. The DFT matrix $F$ has the same four eigenvalues, with multiplicities $m+1, m, m, m-1$ for $N = 4m$, fixed by the trace of $F$, a quadratic [Gauss sum](https://en.wikipedia.org/wiki/Quadratic_Gauss_sum) that Gauss evaluated without the matrix; but nothing canonical plays the oscillator's part for $F$, so a discrete fractional transform is a choice of basis in each eigenspace.[^dftspectrum]

The same group accounts for the FFT. Written out, Cooley–Tukey is two stages of shorter transforms joined by a reindexing and by the [twiddle factors](https://en.wikipedia.org/wiki/Twiddle_factor) $e^{2\pi i ab/N}$, which look like bookkeeping. They are not: the first stage with its reindexing is an intertwiner of two representations of the Heisenberg group, and the twiddle factors are the automorphism $(x, y, t) \mapsto (x, y, xy - t)$ acting on it. Nothing used that $N$ is finite, and the same diagram with $\mathbb{R}$, its subgroup $\mathbb{Z}$ and the quotient circle in the three places of $\mathbb{Z}_N$, its subgroup and its quotient is a proof of Plancherel on the real line.[^atfft]

## Where it gives out

The change of basis of the first course accounts for the intact case, the Gelfand pairs and, via the two-sided action, the non-abelian transforms: fourteen rows. Representation theory keeps six more in the family once diagonalization is gone, by continuing the characters (Laplace, $Z$, chirp $Z$), by intertwining two representations (Radon), and by pairing with the translates of a chosen window (wavelets, Gabor). Two rows mark the boundary. The Hilbert transform is what the method is applied to, not an instance of it. The [Gowers norms](https://en.wikipedia.org/wiki/Gowers_norm) are where the counting above stops. On $\mathbb{Z}_N$ the function $e^{2\pi i x^2/N}$ has every Fourier coefficient of modulus $N^{-1/2}$, as flat as Plancherel allows, yet it and three companions have four-term progression count $1$, the largest possible: the transform is blind to the quadratic phases. There are $N^2$ of them against $N$ characters, so they are no basis, and no quadratic transform or inversion formula exists. What survives is the $U^3$ norm, an average over cubes, and an inverse theorem: a function with large $U^3$ norm correlates with a phase built from a two-step [nilpotent group](https://en.wikipedia.org/wiki/Nilpotent_group), the Heisenberg group of the last section returned in a new role.[^gowers] Nothing is being diagonalized, so the method does not fail there so much as stop applying.

One idea from a first course in linear algebra reaches across two and a half centuries into number theory, tomography, image compression and quantum computation. Representation theory is what one reaches for where it stops, and it works there because diagonalization was one of its tools and never the whole of it.

## Sources

- Lokenath Debnath and Dambaru Bhatta, *Integral Transforms and Their Applications*, 3rd ed., CRC Press, 2015.
- Audrey Terras, *Fourier Analysis on Finite Groups and Applications*, LMS Student Texts 43, Cambridge, 1999.
- Walter Rudin, *Fourier Analysis on Groups*, Interscience.
- Paul R. Halmos, *Finite-Dimensional Vector Spaces*, 2nd ed., Springer UTM.
- Benjamin Steinberg, *Representation Theory of Finite Groups: An Introductory Approach*, Springer Universitext, 2012.
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Harmonic Analysis on Finite Groups*, Cambridge, 2008 (cited as CST 2008).
- Tullio Ceccherini-Silberstein, Fabio Scarabotti and Filippo Tolli, *Discrete Harmonic Analysis*, Cambridge, 2018 (CST 2018).
- Persi Diaconis, *Group Representations in Probability and Statistics*, IMS Lecture Notes 11, 1988.
- Michael A. Nielsen and Isaac L. Chuang, *Quantum Computation and Quantum Information*, Cambridge.
- Greg Kuperberg, *A subexponential-time quantum algorithm for the dihedral hidden subgroup problem*, [arXiv:quant-ph/0302112](https://arxiv.org/abs/quant-ph/0302112), 2003.
- George W. Mackey, *Harmonic analysis as the exploitation of symmetry: a historical survey*, Bull. AMS 3 (1980), 543–698.
- Louis Auslander and Richard Tolimieri, *Is computing with the finite Fourier transform pure or applied mathematics?*, Bull. AMS (N.S.) 1 (1979), no. 6, 847–897 (cited as AT).
- W. T. Gowers, *Generalizations of Fourier analysis, and how to apply them*, Bull. AMS (N.S.) 54 (2017), no. 1, 1–44.

[^dates]: Clairaut 1754, Gauss 1805 and Cooley–Tukey 1965: Terras, pp. xv–xvi and 30–31, after Heideman, Johnson and Burrus (1984); Cooley–Tukey's own paragraphs are quoted in AT, §II.1, p. 871. Laplace in the 1780s, Fourier 1822: Debnath–Bhatta, §1.1. Further: Mackey, §§3–8, for the three origins of harmonic analysis.

[^hankel]: Debnath–Bhatta, §1.1 for the history and Theorem 7.3.4 for $\mathcal{H}_n[\nabla^2 f] = -\kappa^2 \tilde f$. Further: Chapter 7.

[^hadamard]: Terras, p. xvi (Hadamard transform = Fourier on $(\mathbb{Z}/2)^n$) and p. 174 (Walsh functions as reordered Hadamard rows). Further: Nielsen–Chuang, p. 245.

[^mellin]: Debnath–Bhatta, §8.1 for the Riemann–Cahen–Mellin priority and §8.2 for the derivation from the Fourier transform by $x = e^\xi$.

[^frobenius]: Terras, p. 237, for Dedekind's letter and 1897; Mackey, p. 695, for Weyl's recognition in 1927. Further: Mackey, §15, on Peter–Weyl and Cartan.

[^hilbert]: Debnath–Bhatta, Theorem 9.3.1(f): $\mathcal{F}[\mathcal{H}f] = (-i \mathrm{sgn} k) \mathcal{F}[f]$. Further: Chapter 9.

[^radon]: History: Debnath–Bhatta, §1.3. The finite Radon transform on $k$-subsets and its inverse: CST 2008, §6.5, Theorem 6.5.2; intertwiners as bi-invariant functions: Exercise 4.2.5. Further: Debnath–Bhatta, Chapter 18.

[^wavelet]: Debnath–Bhatta, §1.3 for Gabor (1946) and Morlet–Grossmann (1982–84), Definition 19.2.1 and Theorem 19.2.2 for admissibility and the Parseval relation. The comparison with the spherical function $\langle u,\rho(g)u\rangle$ (CST 2008, Cor. 4.6.4) is the present author's.

[^qft]: Nielsen–Chuang, p. 38 for the gate counts, p. 221 for why the amplitudes are not accessible, pp. 245–246 for the history. Further: Chapter 5.

[^halmos]: Halmos, §58 (Jordan form), §79–80 (spectral theorem, self-adjoint and then normal), §84 Exercise 6 (simultaneous diagonalization), §81 (real orthogonal transformations as plane rotations).

[^mackey]: Mackey, §1 for the method, §2 (pp. 547–548) for translation becoming multiplication, §9 (pp. 568–575) for differentiation becoming multiplication, the potential and heat-kernel formulas, which he notes were first obtained by other means (pp. 570–571), and the sphere (p. 574). Further: §23, his summary.

[^rudin]: Rudin, Theorem 1.2.2 and p. 9. Further: Rudin, Chapter 1; for finite groups, Steinberg, Chapter 5.

[^dct]: CST 2008, Appendix 1: the sixteen DCT/DST bases as eigenvectors of path-graph operators obtained by folding under a reflection.

[^dftspectrum]: Continuous case: Debnath–Bhatta, Appendix A-6, (A-6.11)–(A-6.13), for the Hermite functions as an orthogonal basis of $L^2(\mathbb{R})$ with $\mathcal{F}h_n = (-i)^n h_n$ and the oscillator equation they satisfy; the summation of $\sum_n e^{-in\alpha} h_n(t) h_n(u)$ to the chirp is Mehler's formula. Discrete case: CST 2018, Proposition 4.1.2 ($F^4 = I$), Theorem 4.3.1 (Schur's multiplicity table) and §4.4, where the trace of $F$, a Gauss sum, yields quadratic reciprocity. AT, Theorem 1.1.2′, p. 857 (multiplicities, from Schur's $F^2$ = reflection, p. 856), Theorem 1.1.2, p. 855 (Gauss's trace).

[^gelfandpair]: CST 2008, Theorem 4.4.2, Corollary 4.6.4 and Proposition 4.7.2; Steinberg, Example 7.3.5, for $(G,\{1\})$. Further: CST 2008, Chapter 4; Diaconis, Chapter 3F.

[^wedderburn]: Steinberg, Theorem 5.5.6; CST 2008, Theorem 9.5.4, for $(G \times G, \Delta G)$; Kuperberg, §8.2, for row and column spaces. Gowers, §13, pp. 31–33: Plancherel, convolution and inversion with matrix coefficients, and why traces alone span only the class functions.

[^diaconis]: Diaconis, Chapter 3B Lemma 1 (upper bound lemma), 3C Theorem 2 ($\mathbb Z_p$), 3D Theorem 5 (random transpositions); conjugacy classes as canonical forms, p. 14. Cayley graphs: Steinberg, Theorem 5.4.10 (abelian) and Exercise 5.12 (class functions, eigenvalue $\frac{1}{d_\pi}\sum_s \chi_\pi(s)$); the general block statement is Theorem 5.5.6 read on $L(G)$. Further: Diaconis, Chapter 3.

[^laplace]: Debnath–Bhatta, §1.1, p. 2 (why the Laplace transform is easier); Mackey, pp. 550–551 (Laplace's generating functions of 1782, $t^n$ as characters of $\mathbb{Z}$ continued off the circle) and pp. 573–574 (power series as Fourier series of the same kind).

[^fft]: CST 2018, §10.7 and Exercise 10.7.3 (Diaconis–Rockmore, with Cooley–Tukey as the case $K = \mathbb{Z}_m$); §5.4 for Rader, and AT, §III.2, pp. 882–883, for the same rewriting as multiplication in $\mathbb{C}[\mathbb{F}_p^\times]$. Further: CST 2018, Chapter 5.

[^atfft]: AT, §II.1, p. 872 (the diagram), Theorem II.2.1 and pp. 876–877 (the intertwiner; $M$ as the automorphism $K$), §II.3, pp. 877–878 (Plancherel on $\mathbb{R}$).

[^roth]: Gowers, §3, pp. 4–6, including Lemma 3.2 and the iteration. Further: §4, the same proof on $\mathbb{F}_3^n$.

[^gowers]: Gowers, §7, p. 17 (the example), §8, p. 18 ($n^2$ phases, no basis), §11.1, p. 28 (no transform), Theorem 11.2 and pp. 25–27 (inverse theorem, nilsequences, the Heisenberg group). Further: §16, his checklist.

[^hsp]: Nielsen–Chuang, §5.4.3. Kuperberg, §8.2, for the character measurement.

[^heisenberg]: AT, §I.5, Theorems R.1 and R.3 and p. 868 ($F(n)$ intertwines $\rho_1, \rho_2$ and "is essentially determined" by them), §II.2, p. 873 (the group from $\mathbb{Z}_N$, its dual and the pairing); CST 2018, Theorem 12.4.2, for $J$ of order four. Further: CST 2018, §12.5.
