---
title: "Higher Arithmetic Computations"
date: 2021-01-11
permalink: /posts/2021/01/higher-arithmetic-computations/
tags:
  - sagemath
  - python
  - magma
  - open-source
  - number theory
  - arithmetic
  - computations
  - geometry
  - plots
  - sympy
  - matplotlib
  - mpmath
  - numpy
---
In this post I discuss the options available for doing computational experiments in advanced number theory.

# The free rein of proprietary softwares

In the world of mathematical computations, proprietary softwares tend to more adavnced than the open source alternatives. This is mainly because of the lack of industrial support, i.e. nobody can make money by having a better abstract math computation system. Following is the list of current market leaders and their open-source competitors/clones:

| Proprietary software | Speciality | Open-source alternative | Equivalent/complementary [Python libraries](https://wiki.python.org/moin/Libraries) |
|----------|----------| ---------- | --------- |
|SAS/SPSS | Statistical computations | R | statsmodels (NumPy + SciPy + pandas + Patsy + Matplotlib +...)|
|MATLAB | Numerical computations | GNU Octave/Scilab | SciPy (NumPy + Matplotlib + ...) |
|Mathematica/Maple ([Macsyma](https://en.wikipedia.org/wiki/Macsyma))| Symbolic computations (general-purpose CAS) | Maxima/FriCAS (fork of Axiom)  | SymPy (NumPy + Matplotlib + mpmath + ...)|
|Magma | [Structural computations](http://magma.maths.usyd.edu.au/magma/overview/2/19/1/#subsection_1_1) (specialized CAS for mathematical structures from abstract algebra, algebraic geometry and  finite incidence geometry) | SageMath (FLINT, PARI, GAP, Singular, Polymake, CoCoA, Giac, ... glued together using Python) | CyPari2 + ?? |

For a more up-to-date information, have a look at the [ICMS proceedings](https://link.springer.com/conference/icms).

I must point out that RStudio is the only open source alternative which has been able to overtake the proprietary alternatives, mainly because [statistical computations can help you make money](https://gkorpal.github.io/files/bp.pdf). Moreover, though the [Anaconda distribution](https://www.anaconda.com/products/individual) has become the standard open-source alternative to all properitary computational softwares, there still isn't any Python library for "structural computations" (Galois representations, isomorphisms, counting points on varieties, etc.). I believe that this is because SageMath's [motto](https://gkorpal.github.io/files/icms_2010.pdf) "building the car instead of reinventing the wheel" turned it into a bloatware since they [integrated other well developed open source programs](https://doc.sagemath.org/html/en/reference/spkg/) like R, FriCAS, Maxima, and SymPy using Python ([the glue language of scientific computing](https://flow.byu.edu/posts/sci-prog-lang)), instead of just building the Python libraries (like [CyPari2](https://github.com/sagemath/cypari2)) which would act as an [alternative to Magma](https://wiki.sagemath.org/magma), fulfilling the original motto ["Software for Arithmetic Geometry Experimentation"](https://gkorpal.github.io/files/focm11.pdf). To overcome this [failure](https://sagemath.blogspot.com/2014/08/what-is-sagemathcloud-lets-clear-some.html), SageMath evolved into cloud based subscription service called [CoCalc](https://cocalc.com/index.html) to generate revenue for funding the massive project. Howevever, the main contributions seem to be coming from the developments related to the [LMFDB project](https://www.lmfdb.org/acknowledgment). It might also be useful to look at the [ANTS proceedings](https://antsmath.org/). 

# Mix and match

Open source softwares have been a life saver for students in countries like India, where our universities couldn't afford the proprietary softwares. I myself learned numerical analysis on [GNU Octave](https://www.gnu.org/software/octave/) and number theory on [SageMath](https://www.sagemath.org/). Note that, there exist computer algebra systems which follow the philosophy of accepting a given general-purpose programming language and extend it by a set of algebraic capabilities:

| Programming language | CAS library |
| ------------| -------------------- |
| C++ | [SymbolicC++](https://issc.uj.ac.za/symbolic/symbolic.html), [GiNaC](https://www.ginac.de/), [SymEngine](https://github.com/symengine/symengine)|
| Haskell |  [DoCon](https://homepages.inf.ed.ac.uk/wadler/realworld/docon2.html) |
| Python | [SymPy](https://www.sympy.org/en/index.html) | 
| Julia | [Nemo](http://nemocas.org/) (also able to call C/C++ libraries) |

People have tried achieving this in many other programming languages, but all of them are half-baked due to the lack of contributors. In fact, using GiNaC we can get a [symbolic extension](https://wiki.octave.org/wiki/index.php?title=Code&mobileaction=toggle_view_mobile#Octave_interfaces_to_GiNaC) for GNU Octave (nowadays can also [use SymPy](https://github.com/cbm755/octsympy)) and its fork [Pynac](https://github.com/pynac/pynac) provides the backend for symbolic expressions in SageMath (before that Maxima was used).  Moreover, SymEngine is planned to be used as an [optional fast symbolic core for SymPy](https://www.sympy.org/en/roadmap.html) since it is [much faster than Pynac and a bit faster than GiNaC](http://sciruby.com/blog/2015/08/17/ruby-wrappers-for-symengine/). However, for doing computational experiments in higher arithmetic we will have to learn multiple languages:

> Any mathematician who is serious about doing extensive computational work in algebraic number theory and arithmetic geometry is strongly urged to become familiar with all three systems [Sage, Pari and Magma], since they all have their pros and cons. Pari is sleek and small, Magma has much unique functionality for computations in arithmetic geometry, and Sage has a wide range of functionality in most areas of mathematics, a large developer community, and much unique new code. -- [SageMath October 2008 Bordeaux meeting](https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/introduction.html#the-sage-pari-magma-ecosystem)

There is similar advice from Andrew Sutherland and John Voight in [this blog post by Frank Calegari](https://www.galoisrepresentations.com/2020/06/16/tips-on-becoming-a-computational-number-theorist/).

## Python: General-purpose programming language (open-source)

The following has been my journey of learning programming languages so far:

| Education level | Programming language | IDE/Editor (Operating System) |
| --------------- | -------------------- | ---------------------------- |
|Primary school (classes I to IV) | Logo | MSWLogo (Windows 98)|
|Middle school (classes V to VIII) | [BASIC](https://github.com/gkorpal/learning-BASIC_imperative) | Microsoft Small Basic (Windows XP SP3)|
|High school (classes IX to XII) | [Java](https://github.com/gkorpal/learning-Java_GUI) | NetBeans (Windows 7)|
|Undergraduate school | [C++](https://github.com/gkorpal/learning-Cpp_OOP) |Code::Blocks (Ubuntu 14.04)|

<!-----
|Graduate school | Python | Vim with `python-mode` plugin (Fedora 33) | 
----->


During my undergraduate studies, I had the perception that C++ is "the langauge" for scientific computations. In fact, there are many C/C++ libraries for higher arithmetic computations, like [NTL](https://libntl.org), [FLINT](http://www.flintlib.org/), [eclib](http://homepages.warwick.ac.uk/staff/J.E.Cremona/mwrank/), [gf2x](https://gitlab.inria.fr/gf2x/gf2x), [Givaro](https://casys.gricad-pages.univ-grenoble-alpes.fr/givaro/), [GMP](https://gmplib.org/), [GNU MPFR](https://www.mpfr.org/), [GNU MPC](http://www.multiprecision.org/mpc/), [ARB](https://arblib.org/), [CMH](https://gitlab.inria.fr/cmh/cmh#cmh-computation-of-genus-2-class-polynomials), [LinBox](https://linalg.org/), [PARI](http://pari.math.u-bordeaux.fr/), [Symmetrica](http://www.algorithm.uni-bayreuth.de/en/research/SYMMETRICA/), [zn_poly](https://web.maths.unsw.edu.au/~davidharvey/code/zn_poly/), and [m4ri](https://bitbucket.org/malb/m4ri/). However, with the advent of Cython (not to be confused with CPython, which is the original [Python implementation](https://wiki.python.org/moin/PythonImplementations)), Python has become "the new langauge" for scientific computations. The key advantage of Python over C++ is that Python provides better code readability than C++ (like using whitespaces instead of curly braces). In fact, all these C/C++ libraries can now be [accessed via SageMath](https://doc.sagemath.org/html/en/reference/spkg/) using [Python-based syntax](https://doc.sagemath.org/html/en/tutorial/afterword.html). For example, in 2016, Robert J. Lemke Oliver [used SageMath and C++](https://rlemke01.math.tufts.edu/code/primebias.html) to verify the observations by Kannan Soundarajan, leading to the famous discovery of [biases in the distribution of consecutive primes](https://www.quantamagazine.org/mathematicians-discover-prime-conspiracy-20160313/).

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[Python3](https://fedoralovespython.org/) |`python3`|
|[SymPy*](https://developer.fedoraproject.org/tech/languages/python/scipy.html) | `python3-sympy`|
|[CyPARI2](https://pari.math.u-bordeaux.fr/Events/PARI2019/talks/jeroen.html) | `python3-cypari2`|

\*Note that Fedora will automatically install the required dependecies like `mpmath`, `Cython`, `matplotlib` etc.

If you want GUI version of Python development environment then can get [IDLE](https://docs.python.org/3/library/idle.html) by installing the package `python3-idle`. We will use Vim as the text editor for writing [Python scripts](https://docs.python.org/3/tutorial/modules.html). Note that [we don't need](https://unix.stackexchange.com/a/27795/420307) to add a file extension, however for proper syntax highlighting we will use the file extension `.py`. Therefore, it would be helpful to install the `python-mode` plugin ([instructions](https://github.com/python-mode/python-mode)). Following are some the key mappings for some of the `python-mode` commands ([documentation](https://github.com/python-mode/python-mode/blob/develop/doc/pymode.txt)):

| Key mapping | Python-mode command  (normal mode)| Output |
|----------|----------|----------|
| `\\r` | :PymodeRun | Run current code script buffer or selection |
| (<kbd>Ctrl</kbd>+<kbd>w</kbd>) + <kbd>z</kbd> | :pclose | Close the code preview window ([not in doc](https://stackoverflow.com/a/52464433/))|
| <kbd>Shift</kbd> + <kbd>k</kbd> | :PymodeDoc | Show documentation for current word|
| <kbd>Ctrl</kbd> + <kbd>p</kbd> | Usual Vim key binding | Auto-complete a word that has already been typed once in the document|

Note that the text-wrap is disabled by default, with the maximum line length of 79 characters. Moreover, it uses `pylint` to check code at every save. I couldn't figureout how to use code completion via `rope`.

One can learn the basics by going through [Hands-on Python Tutorial](http://anh.cs.luc.edu/python/hands-on/3.1/) by Andrew N. Harrington or skimming through the [tutorial available in the official documentation](https://docs.python.org/3/tutorial/). If you prefer video lectures, then the MIT OCW [Introduction to Computer Science and Programming in Python](https://ocw.mit.edu/6-0001F16) is a good option (many other free tutorials are also there [on YouTube](https://realpython.com/python-youtube-channels/)).

> Python is a [multi-paradigm](https://docs.python.org/3/howto/functional.html), [call by object](https://www.python-course.eu/passing_arguments.php), statically scoped, [both dynamically and strongly typed](https://wiki.python.org/moin/Why%20is%20Python%20a%20dynamic%20language%20and%20also%20a%20strongly%20typed%20language) programming language.

Therefore, though Python is an object-oriented language, it doesn't imply that it doesn't support other programming paradigms ([wikipedia](https://en.wikipedia.org/wiki/Object-based_language)). Also, it would be wise to keep in mind the [floating point arithmetic limitations](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html) that these  general purpose programming languages. For example, if using Python as a calculator, we will get ["wrong" answers when using decimals](https://docs.python.org/3/tutorial/floatingpoint.html):

````python
# Python3 examples
>>> 3.3 - 1.1  # Do not depend on the exactness of floating point arithmetic, even for apparently simple expressions! 
2.1999999999999997
>>> 0.1+0.2  # so here 0.3 is not equal to 0.1 + 0.2
0.30000000000000004
>>> format(.1, '.20f')  # 0.1 does not has exact representation in binary floating point
'0.10000000000000000555'
````
To familiarize yourself with the useful maths libraries in Python (for example, `mpmath` provides support for [arbitrary-precision floating point arithmetic](https://mpmath.org/doc/current/technical.html#decimal-issues), one can use the notes for the [Maths with Python](https://maths-with-python.readthedocs.io/en/latest/index.html) course at the University of Southampton or [Fundamentals of Computer Programming](https://www.math.purdue.edu/~bradfor3/ProgrammingFundamentals/) course by Clinton Bradford at Purdue University. If you prefer video lectures, then the MIT OCW [Introduction to Computational Thinking and Data Science](http://ocw.mit.edu/6-0002F16) is a good option. For example, we can get "correct" answers for float arithmetic by using `decimal` module:

````python
# trying to bypass float arithmetic problem
>>> from decimal import *
>>> Decimal('3.3') - Decimal('1.1')
Decimal('2.2')
>>> Decimal('0.1') + Decimal('0.2')
Decimal('0.3')
>>> Decimal('0.1') == 0.1
False
>>> Decimal('3.5') == 3.5
True
````

### Examples

For elementary numer theory examples, you can use either the course notes for this [(very) short course in Number Theory by Robert Campbell](https://github.com/Robert-Campbell-256/Number-Theory-Python) at the University of Maryland, Baltimore County ([course website](http://www.math.umbc.edu/~campbell/NumbThy/)) or the the companion website for the book ["An Illustrated Theory of Numbers" by Martin H. Weissman](http://illustratedtheoryofnumbers.com/prog.html). However, here we will take some examples from [SageMath](https://sagecell.sagemath.org/) and solve them using Python libraries.

-  Plotting elliptic curves over affine plane

    - SageMath script and output
    ```` python    
    p=plot(EllipticCurve([0,0,0,3,0]), gridlines='true', color=hue(0.7),xmin=-4, xmax=4, ymin=-3, ymax=3, legend_label='$y^2=x^3+3x$')
    p+=plot(EllipticCurve([0,0,0,2,0]), gridlines='true', color='cornflowerblue',xmin=-4, xmax=4, ymin=-3, ymax=3, legend_label='$y^2=x^3+2x$')
    p+=plot(EllipticCurve([0,0,0,1,0]), gridlines='true', color='red',xmin=-4, xmax=4, ymin=-3, ymax=3, legend_label='$y^2=x^3+x$')
    p+=plot(EllipticCurve([0,0,0,-1,0]), gridlines='true', color='orange',xmin=-4, xmax=4, ymin=-3, ymax=3)
    p+=plot(EllipticCurve([0,0,0,-2,0]), gridlines='true', color=hue(0.2),xmin=-4, xmax=4, ymin=-3, ymax=3, legend_label='$y^2=x^3-2x$')
    p+=plot(EllipticCurve([0,0,0,-3,0]), gridlines='true', color=hue(0.3),xmin=-4, xmax=4, ymin=-3, ymax=3, legend_label='$y^2=x^3-3x$')
    p.set_legend_options(shadow=False, loc=2)
    show(p)
    p.axes_labels(['$x$','$y$'])
    p.save('ec.pdf')
    ````
    ![ec](https://gkorpal.github.io/images/sage1.png) 
    
    
    - Python script and output
    
    [to-do](https://stackoverflow.com/questions/19756043/python-matplotlib-elliptic-curves)
    

- Plotting elliptic curve modulo prime

    - SageMath script and output
    
    ```` python
    E=EllipticCurve(GF(1021),[0,-1,-1,0,0])
    A=E.plot()
    show(A)
    A.save('v1.pdf')
    ````
    
    ![ec2](https://gkorpal.github.io/images/sage2.png)
    
    - Python script and output
    
    [to-do](https://github.com/jimmysong/programmingbitcoin/blob/master/ch03.asciidoc)
    
 - Comparing the prime counting functions
 
    - SageMath script and output
    
    ```` python
    P = plot(Li(x), (x,2,10000), linestyle="--", thickness=2, rgbcolor=(0,0,0), legend_label='$\\mathrm{Li}(x)$')
    Q = plot(prime_pi(x), (x,2,10000),thickness=2, rgbcolor=(0,0,0), legend_label='$\\pi(x)$')
    R = plot(x/log(x), (x,2,10000), linestyle=":", thickness=3, rgbcolor=(0,0,0), legend_label='$x/\\log(x)$')
    (P+Q+R)
    ````
    
    ![prime](https://gkorpal.github.io/images/sage5.png)
    
    - Python script and output
    
    [to-do](https://docs.sympy.org/latest/modules/ntheory.html)
    
    
- Plotting Riemann zeta function for real inputs (trivial zeros)

    - SageMath script and output
    
    ```` python
    p=plot(zeta(x), (x,-13,-1), legend_label='$\\zeta(x)$')
    show(p)
    ````
    
    ![ec3](https://gkorpal.github.io/images/sage3.png)
    
    - Python script and output
    
    [to-do](https://docs.sympy.org/latest/modules/functions/special.html#module-sympy.functions.special.zeta_functions)

    
- Plotting  the  real  and  imaginary  parts  of  the  Riemann  zeta  function $\zeta(1/2 + it)$  for $0 < t < 30$

    - SageMath script and output
    
    ````python
    i = CDF.gen()
    v = [zeta(0.5 + n/10 * i) for n in range(300)]
    L = [(z.real(), z.imag()) for z in v]
    line(L)
    ````
    
    ![ec4](https://gkorpal.github.io/images/sage4.png)

- Comparing the argument and absolute values of Riemann zeta function $\zeta(1/2 + it)$  for $0 \leq  t \leq 50$

    - SageMath script and output
    
    ````python
    i = CDF.0
    p1 = plot(lambda t:  arg(zeta(0.5+t*i)), 1, 50,linestyle="--", rgbcolor=(0,0,0), legend_label='$\\mathrm{arg}(\\zeta(0.5+it))$')
    p2 = plot(lambda t:  abs(zeta(0.5+t*i)), 1, 50, rgbcolor=(0,0,0), legend_label='$|\\zeta(0.5+it)|$')
    p1+p2
    ````
    ![prime](https://gkorpal.github.io/images/sage6a.png)

- Plotting complex valued functions

    - SageMath script and output
    
    ```` python
    complex_plot(x^4-1,(-5,5),(-5,5))
    ````
   ![prime](https://gkorpal.github.io/images/sage7.png)

    
- Ideal factorization

    - SageMath script and output
    
    ````python
    K.<a>=NumberField(x^3-19)
    I = K.ideal(3)
    F = I.factor()
    F
    ````
    
    ````
    (Fractional ideal (3, 1/3*a^2 + 1/3*a + 1/3))^2 * (Fractional ideal (3, 1/3*a^2 + 1/3*a - 2/3))
    ````
    
    - Python script and output
    
    [to-do](https://cypari2.readthedocs.io/en/latest/pari_instance.html)
    
    [to-do](https://docs.sympy.org/latest/modules/polys/agca.html)


## Magma: Domain-specific programming language (proprietary)

There exist individual C/C++ libraries, like [FLINT](http://www.flintlib.org/) and [m4ri](https://bitbucket.org/malb/m4ri/wiki/Performance), which are much more efficient than Magma. In fact, Magma itself uses some of the C/C++ libraries like  [ATLAS](http://math-atlas.sourceforge.net/), [GMP](https://gmplib.org/), [GMP-ECM](https://gforge.inria.fr/projects/ecm/), [MPC](http://www.multiprecision.org/mpc/), and [MPFR](http://www.mpfr.org/). However, there aren't enough libraries available to enable SageMath replace Magma completely. 

In the USA, because of the [Simons Foundation Agreement](http://magma.maths.usyd.edu.au/magma/simons_details), you can get access to Magma for free by contacting your department's IT support staff. You should be able to access its full-version on your department's computer clusters and student-version on your personal computer ([installation steps](http://magma.maths.usyd.edu.au/magma/faq/install)). Note that the student-version is available only for the outdated [32-bit architecture](http://magma.maths.usyd.edu.au/magma/download/all/), therefore you might also need to [install additonal packages](https://unix.stackexchange.com/q/75054/) like `glibc.i686` in Fedora ([details](https://stackoverflow.com/a/25269017/)) or `ia32-libs-multiarch` in Ubuntu ([details](https://stackoverflow.com/a/3949268/)). 

We will use Vim as the text editor for writing Magma scripts. Note that, just like for Python scripts, we don't need to add any specific filename extensions to the text files in order to be able to "load them" in Magma ([details](https://gkorpal.github.io/files/magma.pdf)). However, one can use filename extension `.m` to get Objective-C syntax highlighting (`objc.vim`) and to be consistent with the extension used for magma package files ([details](https://gkorpal.github.io/files/msri_magma.pdf)). Moreover, we can run the code without having to leave the text editor by adding the following to `.vimrc` file ([source](https://stackoverflow.com/questions/3166413/execute-a-script-directly-within-vim-mvim-gvim)):

`````vim
map <F2> :w<CR>:!magma %<CR> "once you press <F2> in normal mode, it first saves your file and then run the file with magma.
imap <F2> <Esc>:w<CR>:!magma %<CR> "once you press <F2> in insert mode, it first leaves insert mode, then saves the file and then run the file with magma.
`````

One can learn the basics by going through the ["First Steps in Magma"](http://magma.maths.usyd.edu.au/magma/pdf/first.pdf) or skimming through the first chapter of the ["Handbook of Magma Functions"](http://magma.maths.usyd.edu.au/magma/handbook/part/1), you will be ready to start using Magma for solving math problems. Note that Magma supports the old-school [procedural programming paradigm](https://hackr.io/blog/programming-paradigms) with an ability to implement functional style.

> Magma is an imperative, call by value, statically scoped, dynamically typed programming language, with an [essentially functional subset](https://stackoverflow.com/a/721107/6687333).

### Examples

For some elementary numer theory examples, see the [Micro introduction into Magma](http://legacy-www.math.harvard.edu/computing/magma/index.html) available on the legacy website of Harvard University's Department of Mathematics. However, we will take some examples from [SageMath](https://sagecell.sagemath.org/) and solve them using [Magma](http://magma.maths.usyd.edu.au/calc/). Note that, unlike SageMath, Magma doesn't have access to any plotting library like matplotlib. Therefore, we can't reproduce the graphical examples we saw above.

- Ideal factorization

    - SageMath script and output ([doc](https://doc.sagemath.org/html/en/reference/number_fields/sage/rings/number_field/number_field.html))
    
    ````python
    K.<a>=NumberField(x^3-19)
    I = K.ideal(3)
    F = I.factor()
    F
    ````
    
    ````
    (Fractional ideal (3, 1/3*a^2 + 1/3*a + 1/3))^2 * (Fractional ideal (3, 1/3*a^2 + 1/3*a - 2/3))
    ````
    
    - Magma script and output
    
    ````objc
    R<x>:=PolynomialRing(Integers());
    f:=x^3 - 19;
    K<y>:=NumberField(f);
    O:=MaximalOrder(K);
    I:=3*O;
    Factorization(I);
    `````
    
    ````
    [
    <Prime Ideal of O
    Two element generators:
        [3, 0, 0]
        [2, 0, 2], 1>,
    <Prime Ideal of O
    Two element generators:
        [3, 0, 0]
        [0, 2, 1], 2>
    ]
    ````

# Conclusion

William Stein has played a key role in starting this [open-source mathematical software revolution](https://gkorpal.github.io/files/rnoti-p540.pdf). For example, there exist free online textbooks which use SageMath to teach [elementary number theory](http://math.gordon.edu/ntic/), [linear algebra](http://linear.pugetsound.edu/), [abstract algebra](http://abstract.pugetsound.edu/), [graph theory](https://github.com/rbeezer/eagts), and [game theory](https://nordstromjf.github.io/). However, it would have been great if the academic community could understand the value of [open-source Python-based Magma](https://gkorpal.github.io/files/history.pdf). 

Fortunately, the [OSCAR project](https://oscar.computeralgebra.de/), supported by the German Research Foundation (DFG) since January 2017, has the potential of becoming an [open-source Julia-based Magma](https://arxiv.org/abs/1705.06134). I believe that unlike SageMath, OSCAR will be able to replace Magma, since  like Magma is maintained by the Computational Algebra Group at the University of Sydney, OSCAR is maintained by the Algebra, Geometry and Computer Algebra group at TU Kaiserslautern. Moreover, Julia has simple syntax like Python (Python equivalent is CPython: interpreted language for fast software development), is [as fast as C++](https://julialang.org/blog/2012/02/why-we-created-julia/) (Python equivalent is Cython: compiled language for fast computations) and uses a [LLVM just-in-time (JIT) compiler](https://carolchen.me/blog/jits-intro/#julia-a-jit-compiler-that-s-just-in-time) similar to the [JVM JIT compiler](https://carolchen.me/blog/jits-impls/#an-introduction-to-jvms) of Java (Python equivalent is [PyPy, similar to LuaJIT](https://carolchen.me/blog/jits-impls/#meta-tracing): dynamic language for fast computations). 

In my opinion, the research papers funded by public taxes should be freely available (like free beer) and the softwares needed to do tax-funded research should also be freely available (like free speech). Recently, there has been a surge in researchers using SageMath or Python for doing computations in higher arithmetic. For example, [this arithmetic geometry paper](https://arxiv.org/abs/2004.09046) uses Python for computations.
