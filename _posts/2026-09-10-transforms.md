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

An [integral transform](https://en.wikipedia.org/wiki/Integral_transform), or discrete transform, is a **change of basis**: an operation that re-expresses a function defined on one domain in terms of a different set of basis functions. For a kernel $K(t, u)$, the transform $\mathcal{T}$ of a function $f$ is

$$(\mathcal{T}f)(u) = \int_{D} f(t)\, K(t, u) \, dt$$

where $D$ is whatever the function lives on. That choice is the one which distinguishes one transform from another. $D$ may be an interval of the real line, a ring of $N$ points, where the integral is a sum and the kernel a matrix, the positive reals under multiplication, or the surface of a sphere. What every such domain carries is a symmetry, an operation under which it looks the same from any of its points. That symmetry is a **group**, written $G$, and the third column of the table below names it for each transform in turn.

From Laplace in the 1780s to Gowers norms in the 1990s, the whole zoo is one idea repeated, and the idea does not come from analysis at all. It is a piece of linear algebra that every one of us met in a first course. What follows is an invitation to see how far that one piece reaches, where it finally gives out, and what takes over when it does.

## The transforms in chronological order

| Year | Transform | Domain / Group ($G$) | Kernel | Primary application |
| :--- | :--- | :--- | :--- | :--- |
| **1754** | **[Discrete Fourier Transform (DFT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)** | Cyclic group $(\mathbb{Z}_N, +)$ | $e^{-2\pi i jk/N}$ | Orbit determination, and thereafter the whole of digital signal processing[^clairaut] |
| **1782** | **[Laplace Transform](https://en.wikipedia.org/wiki/Laplace_transform)** | $([0,\infty), +)$, continued to $\Re s > 0$ | $e^{-st}$ | Control theory, ODE stability, circuit analysis[^laplacedate] |
| **1782** | **[Spherical Harmonic Transform](https://en.wikipedia.org/wiki/Spherical_harmonics)** | 2-sphere $S^2 = SO(3)/SO(2)$ | $\overline{Y_\ell^m(\theta,\varphi)}$ | Geopotential models, atomic orbitals, CMB analysis |
| **1805** | **[Fast Fourier Transform (FFT)](https://en.wikipedia.org/wiki/Fast_Fourier_transform)** | Cyclic group $(\mathbb{Z}_N, +)$ | the DFT kernel, rearranged | Telecom, spectral analysis, fast convolution[^fft] |
| **1822** | **[Continuous Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)** | Real line $(\mathbb{R}, +)$ | $e^{-i\omega t}$ | Heat conduction, wave mechanics, quantum theory[^fourierdate] |
| **1875** | **[Hankel Transform](https://en.wikipedia.org/wiki/Hankel_transform)** | Radial functions on $\mathbb{R}^n$, a [Gelfand pair](https://en.wikipedia.org/wiki/Gelfand_pair) | $t\,J_\nu(ut)$ | Axisymmetric boundary value problems, optics, acoustics[^hankel] |
| **1893** | **[Walsh-Hadamard Transform](https://en.wikipedia.org/wiki/Hadamard_transform)** | Hypercube $(\mathbb{Z}_2)^n$ | $(-1)^{\langle x, y \rangle}$ | Error correcting codes, Mariner Mars telemetry, Simon's algorithm[^hadamard] |
| **1896** | **[Mellin Transform](https://en.wikipedia.org/wiki/Mellin_transform)** | Multiplicative reals $(\mathbb{R}^+, \times)$ | $t^{s-1}$ | Analytic number theory, Dirichlet series, asymptotics[^mellin] |
| **1897** | **[Fourier Transform on Finite Groups](https://en.wikipedia.org/wiki/Fourier_transform_on_finite_groups)** | Finite groups: [$S_n$](https://en.wikipedia.org/wiki/Symmetric_group), $D_n$, $GL_2(\mathbb{F}_q)$ | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Representation theory, card shuffling, spectral graph theory[^frobenius] |
| **1905** | **[Hilbert Transform](https://en.wikipedia.org/wiki/Hilbert_transform)** | Real line $(\mathbb{R}, +)$ | $1/\pi(t-u)$, p.v. | Analytic signals, envelope detection, aerofoil theory[^hilbert] |
| **1917** | **[Radon Transform](https://en.wikipedia.org/wiki/Radon_transform)** | Lines in $\mathbb{R}^2$, affine hyperplanes in $\mathbb{R}^n$ | $\delta(u - \langle x, \theta \rangle)$ | CT and PET tomography, seismic imaging[^radon] |
| **1927** | **[Peter-Weyl Transform](https://en.wikipedia.org/wiki/Peter%E2%80%93Weyl_theorem)** | [Compact Lie groups](https://en.wikipedia.org/wiki/Compact_group) $SO(3)$, $SU(2)$ | Matrix coefficients $\overline{\pi_{ij}(g)}$ | Angular momentum, particle physics, molecular replacement |
| **1942** | **[Hartley Transform](https://en.wikipedia.org/wiki/Hartley_transform)** | Real line $(\mathbb{R}, +)$ | $\cos ut + \sin ut$ | Real valued signal processing without complex arithmetic |
| **1946** | **[Gabor Transform / STFT](https://en.wikipedia.org/wiki/Short-time_Fourier_transform)** | Time-frequency plane, the [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) | $\overline{g(t-b)}\,e^{-i\omega t}$ | Spectrograms, speech, time-frequency analysis |
| **1947** | **[Z-Transform](https://en.wikipedia.org/wiki/Z-transform)** | $(\mathbb{Z}, +)$, continued off the unit circle | $z^{-n}$ | Digital filter design (IIR and FIR), sampled-data control[^ztransform] |
| **1969** | **[Chirp Z-Transform (CZT)](https://en.wikipedia.org/wiki/Chirp_Z-transform)** | Spiral contours in $\mathbb{C}$ | $A^{-n}W^{nk}$ | Zoom spectrum analysis, radar |
| **1971** | **[Number-Theoretic Transform (NTT)](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_(general)#Number-theoretic_transform)** | $(\mathbb{Z}_N,+)$ with $\omega$ a [root of unity](https://en.wikipedia.org/wiki/Root_of_unity) in $\mathbb{F}_q^\times$ | $\omega^{jk} \bmod q$ | Exact integer convolution, lattice post-quantum cryptography |
| **1974** | **[Discrete Cosine Transform (DCT)](https://en.wikipedia.org/wiki/Discrete_cosine_transform)** | $\mathbb{Z}_{2N}$, restricted to even extensions | $\cos\frac{\pi k(2n+1)}{2N}$ | JPEG, MPEG, MP3, plausibly the most executed transform ever written |
| **1980** | **[Fractional Fourier Transform (FrFT)](https://en.wikipedia.org/wiki/Fractional_Fourier_transform)** | Phase space rotations $SO(2)$ | chirp, $e^{i\pi[(t^2+u^2)\cot\alpha - 2tu\csc\alpha]}$ | Chirped optical signals, radar filtering[^frft] |
| **1984** | **[Wavelet Transform](https://en.wikipedia.org/wiki/Continuous_wavelet_transform)** | The [affine](https://en.wikipedia.org/wiki/Affine_group), or "$ax+b$", group | $a^{-1/2}\,\overline{\psi((t-b)/a)}$ | JPEG 2000, denoising, LIGO analysis[^wavelet] |
| **1994** | **[Quantum Fourier Transform (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform)** | Cyclic group $(\mathbb{Z}_{2^n}, +)$ | $e^{2\pi i jk/2^n}$ | Shor's factoring algorithm[^qft] |
| **1998** | **[Higher-Order Fourier Analysis](https://en.wikipedia.org/wiki/Gowers_norm)** | $\mathbb{Z}_N$ or $\mathbb{F}_p^n$, with polynomial phases | $e^{2\pi i P(n)}$, $\deg P \geq 2$ | Additive combinatorics, the Green-Tao theorem[^gowers] |

That is the territory. Two and a half centuries, a dozen fields, and no obvious reason why any of these should be thought of together.

The DFT and the FFT raise a question the table does not answer. They are the same transform, so what does the later entry add? Only speed, and the speed comes from the group.

Suppose $N$ is even. The even-numbered points of $\mathbb{Z}_N$ form a subgroup of half the size, and the odd-numbered points are its one other coset. Splitting the sum along that division turns a single transform of length $N$ into two of length $N/2$, plus a cheap step to recombine them. Repeating the split is the fast Fourier transform, and it brings the cost from $N^2$ operations down to $N \log N$.

Notice that the argument never mentions sines or cosines. It uses only the fact that $\mathbb{Z}_N$ has a subgroup to split along, which is why the same manoeuvre gives a fast Walsh-Hadamard transform on $(\mathbb{Z}_2)^n$, a fast spherical harmonic transform, and fast transforms on non-commutative groups. It also says exactly when the manoeuvre is unavailable. If $N$ is prime, $\mathbb{Z}_N$ has no proper subgroup, there is nothing to split, and the recursion never begins. Speed must then be found elsewhere, by rewriting the transform as a convolution and computing that instead. Rader does this for prime $N$, using a convolution of length $N-1$; Bluestein does it for any $N$ using a chirp, which is the same device that appears in the table as the chirp $Z$-transform of 1969. Gauss had the composite case in 1805, and the rediscovery of 1965 is better read as the moment the hardware made it worth having.[^fft]

The quantum Fourier transform invites the opposite error. Writing $N = 2^n$, its circuit uses about $n^2$ gates where the FFT uses about $n 2^n$, an exponential saving which looks like very good news for signal processing. It is no news at all. Measuring a quantum state does not report its amplitudes; it returns a single value, chosen at random with probability given by them. The transformed coefficients are therefore never in hand, and in general the input state cannot be prepared efficiently either. The quantum Fourier transform pays only when what is wanted is one global feature of the spectrum, a period being the standard example, which a single measurement can be made to reveal.[^qft]

Both of those remarks are about speed. A third is about what the speed is for. Nearly every quantum algorithm with an exponential advantage solves a single problem, the [hidden subgroup problem](https://en.wikipedia.org/wiki/Hidden_subgroup_problem): given a function on a group which is constant on the cosets of some unknown subgroup and distinct between them, find the subgroup. [Simon's algorithm](https://en.wikipedia.org/wiki/Simon%27s_problem) is the case $(\mathbb{Z}_2)^n$, and the transform it applies is exactly the Walsh-Hadamard entry above. [Shor's factoring](https://en.wikipedia.org/wiki/Shor%27s_algorithm) is the case of $\mathbb{Z}$, by way of period finding, and it runs on the quantum Fourier transform of 1994. The discrete logarithm is another instance. The family resemblance among the quantum algorithms of the 1990s is not a matter of style. They are one algorithm with different groups put into it.

What that method does, and what it does not, is known fairly sharply. For finite abelian groups it works, in time polynomial in $\log \lvert G \rvert$. For non-abelian groups it largely does not, and the manner of the failure matters here. [Kuperberg (2003)](https://arxiv.org/abs/quant-ph/0302112) reached the dihedral group in subexponential time, $2^{O(\sqrt{\log N})}$, but not by using the dihedral group's own Fourier transform: he applies the ordinary abelian transform to the cyclic subgroup, is left with single-qubit states carrying a known label, and sieves those. The symmetric group, which carries graph isomorphism with it, remains out of reach, and the obstruction there has been shown to be genuine rather than a want of ingenuity. So the non-abelian Fourier transform of 1897 is a real generalization of the abelian one, but it is still the abelian one that does all the algorithmic work.[^hsp]

A fourth remark concerns what the Fourier transform on non-abelian groups is good for when it is not being asked to run an algorithm. A shuffle of $n$ cards is a probability $P$ on $S_n$, and $k$ shuffles is the convolution $P^{*k}$. The convolution theorem and the Plancherel identity, both derived below for abelian groups, survive on a non-abelian group with matrices in place of numbers. The first makes $\widehat{P^{*k}}(\rho) = \hat P(\rho)^k$, and the second turns the [distance](https://en.wikipedia.org/wiki/Total_variation_distance_of_probability_measures) from the uniform distribution $U$ into a sum over the [irreducible representations](https://en.wikipedia.org/wiki/Irreducible_representation) $\rho$:

$$\lVert P^{*k} - U \rVert^2 \le \frac14 \sum_{\rho \neq 1} d_\rho \, \mathrm{Tr}\big(\hat P(\rho)^k \, \hat P(\rho)^{*k}\big)$$

with $d_\rho$ the dimension of $\rho$. Nothing else goes in. Put $\mathbb{Z}_p$ into it, stepping by $\pm 1$, and about $p^2$ steps are needed; put $S_n$ in, swapping a random pair at each step, and $\frac{1}{2} n \log n$ shuffles suffice, the distance staying near $1$ until then and collapsing after, which is the [cutoff phenomenon](https://en.wikipedia.org/wiki/Cutoff_phenomenon). Same lemma, different group.[^diaconis]

What follows argues that one idea from a first course in linear algebra accounts for most of the table, that its limits are worth locating as precisely as its reach, and that the same idea, followed one step past the table, opens into representation theory, which reaches further than it does.

## Transforms as canonical forms

Everybody who has taken a first course in linear algebra has diagonalized a matrix. One chooses a new basis, rewrites the operator in that basis, and the off-diagonal entries vanish. What such a course rarely mentions is that this manoeuvre is one instance of a much older habit, and that the habit has a name.

A **canonical form** is a distinguished representative of an equivalence class, where the equivalence comes from a group acting on the objects in question. Two matrices are similar if $A = P^{-1} B P$, which is to say that they are the same operator written out in two different bases. The canonical form for similarity is the Jordan form, and it is diagonal precisely when the operator has no nilpotent part left over.[^jordan]

Now tighten the equivalence. Require the change of basis to be **unitary**, so that $A \mapsto U A U^{*}$ preserves lengths and angles, $U^{*}$ being the conjugate transpose of $U$. Restrict attention also to normal operators. The canonical form then becomes the diagonal one, and that statement is the spectral theorem.[^spectral]

Here is the whole post in one sentence.

> An integral transform **is** the $U$.

This is meant literally rather than as an analogy. Write $\mathcal{F}$ for the Fourier transform, one particular choice of the $\mathcal{T}$ above, and let $\tau_a$ denote translation by $a$ on the real line, the operator carrying $f(t)$ to $f(t-a)$. Then, with $\xi$ the variable on the transform side,

$$\mathcal{F} \, \tau_a \, \mathcal{F}^{-1} = \text{multiplication by } e^{-i a \xi}$$

Multiplication operators are the diagonal matrices of infinite dimensions, in the sense that each one rescales its input point by point, exactly as a diagonal matrix rescales each coordinate separately. The Fourier transform is therefore the change of basis in which translation becomes diagonal. Most rows of the table above are somebody's choice of $U$, made for a different operator on a different space, and the ones that are not will be worth identifying, because what they give up tells us what the $U$ was doing.

One further theorem explains why a single transform tidies up several operators at once rather than one at a time. Normal operators which commute with one another can be diagonalized **simultaneously**, in one common eigenbasis.[^spectral] Differentiation, translation and convolution commute, so one change of basis serves all three, and the familiar list of properties of the Fourier transform collapses into a single fact.

One qualification has to be entered against all of this, and it is not a small one. **The canonical forms of linear algebra are theorems about matrices**, which is to say about finite dimensions. Half the transforms tabulated above are not finite-dimensional at all, and for them the correspondence has to be restated rather than merely transported.

The difficulty is sharper than a loss of precision. Translation on $\mathbb{R}$ has **no eigenvectors whatsoever** in $L^2(\mathbb{R})$, for the simple reason that $\lvert e^{i \xi t} \rvert = 1$ and a function of constant modulus is not square-integrable. The spectrum is purely continuous and there are no eigenvalues to put on a diagonal. What replaces the diagonal is the multiplication-operator form of the spectral theorem: a normal operator is unitarily equivalent to multiplication by a function on some $L^2(\mu)$, the measure $\mu$ being supplied by the operator itself. That is the sense, and the only sense, in which the continuous Fourier transform diagonalizes anything. Between the two extremes sit the **compact** operators, which retain a genuine diagonal form with eigenvalues tending to zero, and which are therefore the closest infinite-dimensional analogue of the matrix theory.

So much for what a transform does. The question still open is why it should be possible at all, and the answer rests on a single assumption about the domain.

## The one hypothesis behind them all

Something has been passed over. To say that a transform diagonalizes an operator is to leave open which operators it diagonalizes, and the answer is not "any of them". It is completely determined by the domain.

> A transform diagonalizes exactly those operators which **commute with the symmetry of the domain**.

Suppose the domain carries a group action: translation on $\mathbb{R}$, cyclic shift on $\mathbb{Z}_N$, multiplication on $\mathbb{R}^{+}$. The operators commuting with that action are precisely the **convolution operators**, and they commute with one another as well. By the simultaneous diagonalization of the previous section, such a family shares a single eigenbasis, and that eigenbasis consists of the **characters** of the group, a character being a function which converts the group operation into ordinary multiplication, or, in words that will be needed later, a representation of $G$ by $1 \times 1$ matrices.

So the domain settles everything. Name the symmetry and the commuting operators are determined; determine those and their common eigenbasis is determined; and that eigenbasis is the kernel. Nothing in the chain is a matter of choice.

It is worth seeing how little has to be assumed for this to go through. The usual presentations offer a list of properties to be checked off one by one, and any such list invites the reader to suppose that the items are independent of each other. They are not. A single hypothesis suffices, namely that $G$ is a [locally compact abelian group](https://en.wikipedia.org/wiki/Locally_compact_abelian_group), and the standard theory then supplies the rest.[^rudin]

The **dual group**, written $\hat G$, is not a further requirement. It is constructed, the continuous characters of $G$ being shown to form a group in their own right under pointwise multiplication.

A caution on the word "canonical" is in order here, since it is doing two jobs. For a finite abelian group $G$, one has $G \cong \hat{G}$, but **not canonically**: the isomorphism depends on choices. What is canonical is $G \cong \hat{\hat{G}}$, and that statement, [Pontryagin duality](https://en.wikipedia.org/wiki/Pontryagin_duality), is the one which deserves the name.

The **convolution theorem** is a single line, and it uses nothing about a character $\chi$ beyond the fact that it is a homomorphism. Writing $\hat f$ for $\mathcal{F}f$, which is the customary shorthand, $f * g$ for the convolution of $f$ with $g$, and a bar for complex conjugation:

$$\widehat{f * g}(\chi) = \iint f(x) g(y) \overline{\chi(xy)} \, dx \, dy = \hat f(\chi) \, \hat g(\chi)$$

The **Plancherel isometry** is likewise a theorem rather than a stipulation, once the [Haar measure](https://en.wikipedia.org/wiki/Haar_measure) on the dual group is normalized to match the one on $G$.

The result which packages all three together has a name. Under convolution the space $L^1(G)$ is a commutative Banach algebra, and its maximal ideal space turns out to be precisely the dual group: the characters are exactly the non-zero complex homomorphisms of that algebra, and the Fourier transform is its [Gelfand transform](https://en.wikipedia.org/wiki/Gelfand_representation). That is the abstract form of the argument made by hand a few paragraphs above, since the multiplicative functionals of a commutative algebra play the part that common eigenvectors play for a commuting family of operators.

So there is nothing to check off, and nothing to be verified transform by transform. There is one hypothesis. The group is chosen first, and the kernel is then forced rather than selected.

When the hypothesis holds in full, that is the whole story. The characters of $G$ supply the kernel and the canonical form is diagonal. That is the case of the **DFT** and its fast evaluation the **FFT**, the **continuous Fourier transform**, the **Mellin transform**, the **Walsh-Hadamard transform**, the **DCT**, the **QFT**, and the **fractional Fourier transform**, whose one-parameter group of rotations is abelian and which is diagonal in the Hermite basis. Call this the **intact case**. Everything that follows is measured against it.

Which raises the obvious question. If everything rests on that one assumption, what becomes of a transform whose domain does not satisfy it?

## Seven departures

The rest of the family is what survives when some part of the hypothesis is surrendered.

> Every other member of the family is a departure from that one hypothesis.

There are seven such departures, set out below in order of decreasing strength.

1. **Block diagonal, with small blocks.** Drop commutativity. When $G$ is non-abelian its characters are no longer numbers, and the definition given above stops applying. They become matrix coefficients of irreducible representations, meaning the smallest matrix-valued symmetries the group admits, and convolution becomes pointwise *matrix* multiplication within each one. The blocks are as large as those representations. This is a genuine generalization rather than a failure, and it is how the **Fourier transform on finite groups** and the **Peter-Weyl transform** stay in the family.

2. **Block diagonal, on account of the field.** Keep the group, but insist that the change of basis be real. The cyclic shift has the $N$th roots of unity as eigenvalues, and a real basis cannot separate a conjugate pair, so the best available real form is a string of $2 \times 2$ rotation blocks.[^realorth] The **Hartley transform** attains exactly that. Its kernel $\cos\nu x + \sin\nu x$, written $\mathrm{cas}\,\nu x$, satisfies $\frac{d}{dx}\mathrm{cas}\,\nu x = \nu\,\mathrm{cas}(-\nu x)$, and so pairs $\nu$ with $-\nu$. What looks like a defect is no defect. No real transform can do better. Changing the field need not cost anything, mind: the **NTT** works over $\mathbb{F}_q$ and recovers a full diagonal, provided $N$ divides $q-1$.

3. **Diagonal, but only after analytic continuation, and with unitarity surrendered.** The function $e^{-st}$ with $\Re s > 0$ is not a character of $(\mathbb{R},+)$. It is a character continued off the axis where the characters live, which is why it decays rather than oscillating. The **Laplace transform** is therefore a special case of the Fourier transform, taken over functions on the positive real axis, and the easier of the two to handle, since a decaying kernel makes convergence almost automatic.[^laplace] The price is Plancherel: there is no isometry, and inversion needs a contour integral. The **$Z$-transform** strikes the identical bargain on $\mathbb{Z}$, and the **chirp $Z$-transform** is the same object again, evaluated along a spiral rather than a circle.

4. **No group at all, but a Gelfand pair instead.** Radial functions on $\mathbb{R}^n$, and functions on the sphere $S^2 = SO(3)/SO(2)$, live on homogeneous spaces rather than groups. A Gelfand pair is the next best thing: a group together with a subgroup, arranged so that the convolution algebra comes out commutative even though no commutative group underlies it. The **Hankel transform** and the **spherical harmonic transform** are of this kind.

5. **Intertwining rather than conjugation.** The **Radon transform** $\mathcal{R}$ gives up on $U A U^{-1}$ entirely. It settles for a relation between two different operators living on two different spaces, namely $\mathcal{R}(\Delta f) = \partial_s^2 (\mathcal{R} f)$, where $\Delta$ is the Laplacian on the original space and $s$ the offset of the line along which $\mathcal{R}$ integrates. What it keeps is the symmetry: the rigid motions of the plane act on points and on lines alike, and $\mathcal{R}$ respects both actions.

6. **No diagonalization, but the isometry survives.** The **wavelet transform** and the **Gabor transform** keep a group, the affine group and the Heisenberg group, but give up its characters, and any clean convolution theorem with them. What survives is energy. An admissibility condition on the analysing window still guarantees that the whole family of shifted and scaled copies adds up to the identity, so nothing is lost in the transform. Isometry, it turns out, is the last thing to go. The characters may be abandoned and the convolution theorem with them, and Plancherel will still be standing. Why it stands is a question the canonical-form picture cannot answer, and it is taken up below.

7. **Nothing linear at all.** **Higher-order Fourier analysis** replaces characters with polynomial phases, and its Gowers norms detect structure of degree two and above, to which linear characters are provably blind.

That accounts for every row of the chronological table but one. The **Hilbert transform** sits at no position on the scale, because it is not a change of basis at all. It is a convolution operator which the Fourier transform diagonalizes, which makes it something the method is applied to rather than an instance of the method.[^hilbert]

Departure 2 repays being spelled out, because it accounts for three rows of the chronological table in one stroke. The [Frobenius normal form](https://en.wikipedia.org/wiki/Frobenius_normal_form), or rational canonical form, decomposes any matrix over any field into [companion](https://en.wikipedia.org/wiki/Companion_matrix) blocks. The cyclic shift on $\mathbb{Z}_N$ is the companion matrix of $x^N - 1$, so the [circulant matrices](https://en.wikipedia.org/wiki/Circulant_matrix) are the ring $K[x]/(x^N-1)$, and the transform one obtains is decided by how $x^N - 1$ factors over the field in question.

| Field $K$ | How $x^N - 1$ factors | Best canonical form | Transform |
| :--- | :--- | :--- | :--- |
| $\mathbb{C}$ | into $N$ distinct linear factors | Diagonal | **DFT** |
| $\mathbb{R}$ | into $x - 1$, and $x + 1$ when $N$ is even, together with quadratics $x^2 - 2\cos(2\pi k/N)\,x + 1$ | $2 \times 2$ rotation blocks | **Hartley** |
| $\mathbb{F}_q$ | into distinct linear factors exactly when $N$ divides $q-1$ | Diagonal over $\mathbb{F}_q$ | **NTT** |

One module, three fields, three transforms.[^eight]

## From one operator to a family

A canonical form was defined at the outset as a distinguished representative of an equivalence class, the equivalence coming from a change of basis. Everything so far has applied that definition to one operator at a time, or to a commuting family, which is nearly the same thing. Drop the word "commuting" and the definition does not change, but the subject does. A family of matrices, one for each element of a group $G$ and multiplying as the group does, is a [representation](https://en.wikipedia.org/wiki/Group_representation) of $G$, and two representations are equivalent when one change of basis carries every matrix of the first to the corresponding matrix of the second. Representation theory is the theory of canonical forms for such families, and it opens with the same two theorems this note opened with.

The first is the spectral theorem, in the form it takes when the operators no longer commute. For a finite group, [averaging over $G$](https://en.wikipedia.org/wiki/Maschke%27s_theorem) gives every invariant subspace an invariant complement, so a representation breaks into a direct sum of irreducible ones; [Schur's lemma](https://en.wikipedia.org/wiki/Schur%27s_lemma) makes the decomposition unique; and the [character](https://en.wikipedia.org/wiki/Character_theory), the function $g \mapsto \mathrm{tr}\, \rho(g)$, determines the representation entirely.[^fhfinite] The irreducibles are the eigenspaces, the multiplicities are the multiplicities, and the character is the spectrum: a complete invariant, computed by taking traces. It is also why the word "character" has meant a number in this note and now means a trace. For an abelian group every irreducible is one-dimensional, the trace is the entry, and the two meanings coincide.

The second is the Jordan form, in the role it has had throughout, of marking where the method fails. The averaging needs to divide by $\lvert G \rvert$, and there are two ways for that to be impossible. The group may be infinite and non-compact, so that there is nothing to average over: the real line acting on the plane by $t \mapsto \begin{pmatrix} 1 & t \\ 0 & 1 \end{pmatrix}$ fixes the $x$-axis and admits no complementary invariant line, which is to say that it is a Jordan block and no basis improves it. Or the field may have characteristic dividing $\lvert G \rvert$, so that the average divides by zero; this is [modular representation theory](https://en.wikipedia.org/wiki/Modular_representation_theory), and it is hard for the same reason that a repeated pole is untidy in the Laplace domain, where it inverts to $t^k e^{\lambda t}$, which is a Jordan block, which is [resonance](https://en.wikipedia.org/wiki/Resonance).[^fhfinite] Resonance, the non-compact group and the finite field are one defect, a nilpotent part with nowhere to go, met three times.

Where in this is the transform? In the group algebra. The [group algebra](https://en.wikipedia.org/wiki/Group_ring) $\mathbb{C}[G]$ is the space of functions on $G$ under convolution, and its canonical form as an algebra is $\bigoplus_\rho \mathrm{End}(W_\rho)$, one full matrix algebra for each irreducible representation. The isomorphism is the Fourier transform on $G$; the convolution theorem, the inversion formula and the Plancherel identity are what one checks to see that it is.[^fhgroupalgebra] The card-shuffling remark below the first table used nothing else. So departure 1 was never a departure from representation theory. It was representation theory, and the abelian transforms are the case in which every block is $1 \times 1$.

The same recipe runs one level further, for continuous symmetry, and there it is stated as a recipe. A [Lie algebra](https://en.wikipedia.org/wiki/Lie_algebra) is a family of matrices closed under commutators, and a [semisimple](https://en.wikipedia.org/wiki/Semisimple_Lie_algebra) one is analysed by finding a maximal commuting family inside it that acts diagonalizably, called a [Cartan subalgebra](https://en.wikipedia.org/wiki/Cartan_subalgebra), diagonalizing that family simultaneously, which is the same theorem that served the convolution operators, and reading off the joint eigenvalues. Those eigenvalues are linear functionals on the Cartan subalgebra, characters in all but name, and they are called [roots](https://en.wikipedia.org/wiki/Root_system) when the algebra acts on itself and [weights](https://en.wikipedia.org/wiki/Weight_(representation_theory)) when it acts on anything else; the rest of the algebra shifts one joint eigenspace to another, as multiplication by a character shifts the Fourier side. Semisimplicity is the hypothesis that makes this go through, and it is the same word as before. A [nilpotent Lie algebra](https://en.wikipedia.org/wiki/Engel%27s_theorem) can be made triangular and no better, and the [Jordan splitting](https://en.wikipedia.org/wiki/Jordan%E2%80%93Chevalley_decomposition) of an element into diagonalizable and nilpotent parts is intrinsic to the algebra when the algebra is semisimple, and need not be otherwise.[^fhlie]

Passing from the single operator to the family also collects what the departures left behind, and that is the strongest reason for doing it. Departures 5 and 6 were where the canonical-form picture gave out, and both are ordinary representation theory. The Radon transform respects the rigid motions acting on points and on lines at once, which makes it an [intertwining operator](https://en.wikipedia.org/wiki/Equivariant_map) between two representations of the same group, and the identity $\mathcal{R}\Delta = \partial_s^2 \mathcal{R}$ is what such an operator must do to the invariant differential operator on each side. The wavelet and Gabor transforms are the numbers $\langle f, \pi(g)\psi \rangle$, the [matrix coefficients](https://en.wikipedia.org/wiki/Matrix_coefficient) of a representation $\pi$ of the affine or Heisenberg group taken against one fixed vector $\psi$, and the admissibility condition that kept their isometry alive is the [orthogonality relation](https://en.wikipedia.org/wiki/Schur_orthogonality_relations) for those coefficients, the same relation which, for a finite group, makes the matrix entries of the irreducible representations an orthogonal basis for all functions on $G$.[^sqint] That is why Plancherel was the last thing to go: it never depended on the characters, only on the representation. The Laplace and $Z$ transforms use characters continued off the unitary axis, which are representations still, only non-unitary ones, and the Hartley transform uses the real representations of an abelian group, where a character and its conjugate pair off. Count again. The chronological table has twenty-two rows; seventeen of them are a canonical form, and twenty are representation theory. The two outside both pictures are the Hilbert transform, which is an operator rather than a change of basis, and the Gowers norms, which are not linear. So the family reaches three rows further than the single operator, and it reaches them because diagonalization is one of its tools rather than the whole of it: it also has intertwiners, matrix coefficients as functions, and representations that are not unitary.

So the chain that runs from a first course in linear algebra to its canonical forms and from there to the transforms has a fourth link, the representations, and the flow along it runs one way, from the method to its instances. Canonical forms are the method. Representation theory is the larger of its two applications here, and the transforms are instances of representation theory in turn, each one a group and a choice of what to compute from its irreducible representations. A normal operator, a finite group over $\mathbb{C}$, a compact group, a semisimple Lie algebra: in each case a canonical form exists and is diagonal or block diagonal, and in each case for the same reason, that nothing nilpotent survives. The one hypothesis of the earlier section, that $G$ be locally compact abelian, is the commutative instance of that condition, and the seven departures are seven ways of keeping enough of it to have a canonical form worth writing down, or, for Radon and the wavelets, of keeping a representation when no canonical form is left.

## Back to canonical forms

These notes began with diagonalization, arrived at seven ways of falling short of it, and then found the same idea waiting one level up. It remains to close the circle, by going back to the linear algebra and asking how much of it has been used. The standard list of canonical forms is short and well known; the [Wikipedia summary](https://en.wikipedia.org/wiki/Canonical_form#Linear_algebra) is as good a version of it as any. Set that list beside the twenty-two and most of it turns out to be occupied. Some rows name a transform that somebody uses in earnest. The rest mark a boundary: the place where the method fails, the lattices it touches only in passing, and the plain fact about dimension which makes a change of basis mean anything at all. Four rows can also be read for a family, and the previous section is the reason they can.

The dictionary below is arranged by relevance to the present discussion rather than by any standard ordering. Two of the usual entries, the Weyr and Howell forms, are omitted, since neither carries a useful counterpart here. One entry which does not normally appear on such lists, the Wedderburn decomposition, has been added, since it is the one that matters most here; its row says why it is usually missing. The last column is filled only where a named theorem of representation theory is the same statement, and says so where there is none.

| Normal form | Canonical form of | Transform | Representation theory |
| :--- | :--- | :--- | :--- |
| **[Diagonal](https://en.wikipedia.org/wiki/Spectral_theorem)** (spectral theorem) | Normal matrices, under unitary similarity | The DFT and the other abelian Fourier transforms, which is the intact case. In infinite dimensions the diagonal has to be read as a multiplication operator | Maschke and Schur for abelian $G$: every irreducible is one-dimensional, so a representation is a commuting family and diagonalizes at once |
| **[Frobenius](https://en.wikipedia.org/wiki/Frobenius_normal_form)**, or rational | Any matrix over a field, under similarity, decomposed into companion blocks | The DFT, Hartley and the NTT at once, by the field table above. Over $\mathbb{C}$ it is the diagonal row, which is why the DFT appears twice | A single operator is a $K[x]$-module, that is, a representation of $\mathbb{Z}$ over $K$; the cyclic shift is $K[\mathbb{Z}_N] = K[x]/(x^N-1)$ |
| **[Block diagonal](https://en.wikipedia.org/wiki/Artin%E2%80%93Wedderburn_theorem)**, Wedderburn | The group algebra $\mathbb{C}[G]$, as an algebra | Fourier on a finite group, departure 1, abelian exactly when every block is $1 \times 1$. Missing from the usual lists because it classifies algebras rather than matrices | Maschke and Schur in general: $V \cong \bigoplus_\rho a_\rho W_\rho$, uniquely, and $\mathbb{C}[G] \cong \bigoplus_\rho \mathrm{End}(W_\rho)$ |
| **[Jordan](https://en.wikipedia.org/wiki/Jordan_normal_form)** | Matrices over an algebraically closed field, under similarity | Where the method fails. A repeated pole in the Laplace domain produces $t^k e^{\lambda t}$, which is a Jordan block, which is resonance | Where Maschke fails: the non-compact group, and the field of characteristic dividing $\lvert G \rvert$ |
| **[Smith](https://en.wikipedia.org/wiki/Smith_normal_form)** | Matrices over a principal ideal domain | The structure theorem for finite abelian groups, hence every finite abelian Fourier transform is a tensor product of cyclic DFTs. The mixed-radix FFT follows the same factorization | Nothing beyond the previous column: the characters of a product are the products of characters |
| **[Singular value decomposition](https://en.wikipedia.org/wiki/Singular_value_decomposition)** | Any complex matrix, under unitary equivalence | The [Karhunen-Loève transform](https://en.wikipedia.org/wiki/Karhunen%E2%80%93Lo%C3%A8ve_theorem), that is, PCA. The DCT is its asymptotic form for first-order Markov sources, which is much of the reason JPEG uses it | Not applicable. No group acts; the SVD is what one does when there is no symmetry to hand |
| **[Hermite](https://en.wikipedia.org/wiki/Hermite_normal_form)** | Integer matrices, under unimodular multiplication | The canonical basis of a [lattice](https://en.wikipedia.org/wiki/Lattice_(group)). It fixes the sampling lattice in multidimensional signal processing, and separately it is used to put lattice cryptosystem keys into standard form | Not applicable |
| **[$K^n$](https://en.wikipedia.org/wiki/Dimension_theorem_for_vector_spaces)** | Finite-dimensional vector spaces, under isomorphism | Why "change of basis" means anything at all. For finite $G$ of order $N$, $L^2(G)$ is merely $\mathbb{C}^N$, so a transform is a change of basis within one space rather than a map between two. Plancherel says that the basis is orthonormal | Not applicable |

## Where it gives out

One caution about those seven departures. They rank transforms by how much of a single linear-algebra idea survives in each, and that is not a ranking of the transforms. Radon, Gabor, wavelets and the Gowers norms come last on it because diagonalization is not what they are built to do. One recovers a function from its projections, two resolve time and frequency together, and the last detects quadratic structure to which linear characters are provably blind. No such goal is served by putting an operator into diagonal form, so a transform which pursues one of them is not failing at diagonalization; it is doing something else. For three of the four, the something else is still representation theory, as the previous section showed. Only the Gowers norms, and the Hilbert transform which was never on the scale, lie outside both pictures.

Which is the whole of the invitation. One idea from a first course in linear algebra reaches across two and a half centuries and into number theory, tomography, image compression and quantum computation, and then it stops, five rows short of the table. The subject it opens into, the representation theory of groups, reaches three rows further, because diagonalization is one of its tools and not the whole of it. Knowing where the first idea stops is what tells you when to reach for the second.

## Sources

Written by Claude. An AI slop.

- Walter Rudin, *Fourier Analysis on Groups*, Interscience. Chapter 1 for the whole of the abstract theory used here: Haar measure, the dual group, the Plancherel theorem, Pontryagin duality, and the identification of the dual group with the maximal ideal space of $L^1(G)$.
- Paul R. Halmos, *Finite-Dimensional Vector Spaces*, Springer UTM. The canonical forms, the spectral theorem, and commuting families of normal operators.
- Lokenath Debnath and Dambaru Bhatta, *Integral Transforms and Their Applications*, 3rd edition, CRC Press, 2015. The historical introduction and the chapters on the Hankel, Mellin, Hilbert, $Z$ and Radon transforms.
- Audrey Terras, *Fourier Analysis on Finite Groups and Applications*, LMS Student Texts 43, Cambridge, 1999. The abelian and non-abelian dictionary, the group algebra and Wedderburn, Hadamard and Walsh, and the Gauss and Clairaut prehistory of the FFT.
- Persi Diaconis, *Group Representations in Probability and Statistics*, IMS Lecture Notes–Monograph Series 11, 1988. Chapter 3 for random walks on groups, the upper bound lemma, and random transpositions.
- William Fulton and Joe Harris, *Representation Theory: A First Course*, Springer GTM 129, 1991. §1.2 for complete reducibility and Schur's lemma, §2.2 for the character as a complete invariant, §3.4 for the group algebra as the Fourier transform, §9.2 and §9.3 for the triangular forms and the Jordan decomposition, and §14.1 for the analysis of a semisimple Lie algebra by a Cartan subalgebra.
- Michael A. Nielsen and Isaac L. Chuang, *Quantum Computation and Quantum Information*, Cambridge. Chapter 5 for the quantum Fourier transform, phase estimation, and the hidden subgroup problem.
- George W. Mackey, *Harmonic analysis as the exploitation of symmetry: a historical survey*, Bulletin of the AMS 3 (1980). The thesis of the last two sections, that the transforms are instances of representation theory, stated at length and with the history.
- Sigurdur Helgason, *The Radon Transform*, 2nd edition, Birkhäuser, 1999. Chapter I for the Radon transform as an intertwining operator and its relation to the Laplacian.


[^rudin]: Rudin, *Fourier Analysis on Groups*, Chapter 1: Haar measure §1.1.1, the dual group §1.2, Plancherel §1.6, Pontryagin duality §1.7. The identification is stated on p. 7, and Theorem 1.2.2 proves it both ways, each character giving a non-zero complex homomorphism of $L^1(G)$ and every such homomorphism arising so. Rudin's proof is the convolution computation displayed above. He writes $\Gamma$ where these notes write $\hat G$.

[^jordan]: The standard treatment is Halmos, *Finite-Dimensional Vector Spaces*, §58, where the Jordan form is introduced under the older name of the classical canonical form. The criterion for diagonality is stated there in terms of the chains of ones above the diagonal, all of which must be empty.

[^spectral]: Halmos, §79 for the spectral theorem itself, and §84 for the simultaneous diagonalization of a commuting family of normal transformations, which he leaves as an exercise. Both statements are finite-dimensional, and the qualification that this entails is set out at the end of the same section in which they are used.

[^realorth]: Halmos, §81. Each block is a plane rotation, with entries $\cos\theta$ and $\pm\sin\theta$. Every conjugate pair of eigenvalues contributes one such block, and no real basis can separate a pair.

[^eight]: Worth checking by hand. For $N = 8$ the real factorization is $(x-1)(x+1)$ together with three quadratics $x^2 - 2\cos(2\pi k/8)x + 1$, and the Hartley transform duly reduces the shift to two single entries, $+1$ and $-1$, and three rotation blocks, through $45$, $90$ and $135$ degrees.

[^laplace]: Debnath and Bhatta §1.1, which gives three reasons for the relative simplicity: the decaying kernel makes convergence far less delicate, the transform is analytic in $s$ so that complex variable theory applies directly, and the Fourier integral formula supplies the inversion as a contour integral.

[^clairaut]: Heideman, Johnson and Burrus (1984), as reported in Terras, *Fourier Analysis on Finite Groups*, pp. xv to xvi: Clairaut used the DFT in 1754 for the determination of orbits, which is earlier than Fourier's work on Fourier series. The conventional date of 1805 belongs to the *fast* algorithm rather than to the transform.

[^laplacedate]: Debnath and Bhatta §1.1 place the origin in Laplace's work on probability "in the 1780s", with the results appearing in *Théorie Analytique des Probabilités* (1812). Euler had used the integral decades earlier. The date 1782 is conventional rather than decisive.

[^fft]: Terras, pp. xv and 130. Gauss was computing the orbit of the asteroid Juno; Cooley and Tukey (1965) are the usual credit. The recursive product formula behind the method was known to Danielson and Lanczos earlier still, according to Nielsen and Chuang.

[^fourierdate]: Fourier's memoir of 1807 concerns Fourier *series* on a finite interval. Debnath and Bhatta §1.1 record that "in an attempt to extend his new ideas to functions defined on an infinite interval, Fourier discovered an integral transform and its inversion formula", which is the prize essay of 1811 and the *Théorie analytique de la chaleur* of 1822. Cauchy and Poisson arrived independently at the same transformation.

[^hankel]: Hankel died in 1873, and the paper on Fourier series and integrals for cylinder functions appeared posthumously in *Mathematische Annalen* 8 (1875). Debnath and Bhatta §7.1 note that the transform "can easily be derived from the two-dimensional Fourier transform when circular symmetry is assumed".

[^hadamard]: Three dates, one transform: Sylvester's recursive construction of 1867, Hadamard's study of the matrices in 1893, Walsh's function system of 1923. Terras is blunt that these are not distinct objects, engineers saying "Hadamard transform" where mathematicians say "Fourier transform on $(\mathbb{Z}/2\mathbb{Z})^n$" (p. xvi), the Walsh functions being a reordering of the rows of the Hadamard matrix (p. 174). The $n$-qubit gate $H^{\otimes n}$ is the same transform again, which makes it the earliest quantum Fourier transform, predating Shor by nearly a decade.

[^mellin]: Debnath and Bhatta §8.1 give the chain of priority: Riemann first recognized the transform in his memoir on prime numbers, Cahen (1894) gave the explicit formulation, and Mellin (1896, 1902) supplied the elaborate treatment together with the inversion formula.

[^frobenius]: Terras, p. 237, dates the creation of non-abelian representation theory to 1897, prompted by Dedekind's letter asking Frobenius to factor the group determinant $\det(m(gh^{-1}))$. Frobenius's *Über Gruppencharaktere* is dated 1896, and both dates are in circulation. It is a pleasing accident that the rational canonical form carries the same name.

[^hsp]: Nielsen and Chuang, §5.4.3, for the framework and the abelian case; their account predates the rest. Kuperberg, *A subexponential-time quantum algorithm for the dihedral hidden subgroup problem* (2003); the reduction to the abelian transform and the sieve is set out cleanly in Andrew Childs's lecture notes on the dihedral HSP. The obstruction for the symmetric group is Moore, Russell and Schulman, *The symmetric group defies strong Fourier sampling* (2005), which rules out any measurement of one or two coset states.

[^qft]: Four steps rather than one, following Nielsen and Chuang's history section, and the gate counts and the caveat above are theirs. Deutsch (1985) handled $(\mathbb{Z}_2)^n$; Shor (1994) did $\mathbb{Z}_m$ for certain $m$; Coppersmith (1994), with Deutsch and Cleve, gave the standard circuits over $\mathbb{Z}_{2^n}$; Kitaev (1995) generalized to any finite abelian group and introduced phase estimation.

[^hilbert]: Named for Hilbert, though Debnath and Bhatta §1.1 observe that the transform and its properties "are basically studied by G. H. Hardy and E. C. Titchmarsh". It sits awkwardly in the chronological table because it is less a change of basis than a convolution operator which the Fourier transform diagonalizes.

[^radon]: Radon (1917) reconstructed a function of two variables from its integrals over all straight lines in the plane, and then generalized to integrals over smooth curves. The hyperplane version in $n$ dimensions came later. The application of Cormack and Hounsfield to CT won the Nobel Prize in Physiology or Medicine in 1979.

[^ztransform]: Hurewicz (1947); the name is due to Ragazzini and Zadeh (1952). The standard references are Jury, *Theory and Application of the Z-Transform* (1964) and Zadeh and Desoer, *Linear System Theory* (1963).

[^frft]: Namias (1980), with substantial precursors in Wiener (1929) and Condon (1937).

[^wavelet]: Debnath and Bhatta record that the wavelet transform was discovered by Jean Morlet, a French geophysical engineer; Alex Grossmann recognized its importance, and their collaboration produced the mathematical theory of the continuous wavelet transform. Haar's basis of 1909 is the retrospective ancestor.

[^gowers]: Gowers (1998) for progressions of length four, the general case following in 2001. The Gowers $U^k$ norms detect polynomial structure of degree $k-1$, which linear characters cannot see.

[^diaconis]: Diaconis, Chapter 3B, Lemma 1, p. 24, the upper bound lemma, proved by Cauchy-Schwarz and Plancherel; the circle is Theorem 2, p. 25, and random transpositions Theorem 5, p. 36. Terras states the abelian case as Lemma 2 of Chapter 6, p. 112, and the general one as Lemma 1 of Chapter 17, p. 287, with the proof left as an exercise.

[^fhfinite]: Fulton and Harris, §1.2, pp. 6 to 7: Corollary 1.6 (complete reducibility), Schur's Lemma 1.7 and Proposition 1.8 (uniqueness), with the unipotent action of $\mathbb{R}$ and the remark on modular representations on the same pages. Corollary 2.14, p. 17, reads in full "Any representation is determined by its character."

[^fhgroupalgebra]: Fulton and Harris, Proposition 3.29, p. 37, with the remark that the isomorphism "can be interpreted as the Fourier transform"; Exercise 3.32, p. 38, is the convolution theorem, inversion and Plancherel. Diaconis proves the same three on p. 13.

[^sqint]: Grossmann, Morlet and Paul, *Transforms associated to square integrable group representations*, J. Math. Phys. 26 (1985), which introduces the wavelet transform as a matrix coefficient and derives admissibility from the orthogonality relations of Duflo and Moore (1976). The Radon transform as an intertwining operator for the group of rigid motions is Helgason, *The Radon Transform*, Chapter I. The general thesis, that harmonic analysis is the representation theory of the symmetry group, is Mackey, *Harmonic analysis as the exploitation of symmetry*, Bull. AMS 3 (1980), which Diaconis's annotated bibliography singles out.

[^fhlie]: Fulton and Harris, §14.1, pp. 197 to 199, Steps 0 to 2, the justification for Step 1 being given on p. 162. Engel and Lie are Theorems 9.9 and 9.11, pp. 125 to 126; the Jordan decomposition in a semisimple Lie algebra is Theorem 9.20, p. 129, with the one-dimensional counterexample just before it.

