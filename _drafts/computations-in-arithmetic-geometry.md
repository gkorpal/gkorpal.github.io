---
layout: single
title:  "Computations in Arithmetic Geometry"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
In this post I discuss the options available for doing computational experimentation in arithmetic geometry.

# The free rein of proprietary softwares

In the world of mathematical computations, proprietary softwares tend to more adavnced than the open source alternatives. This is mainly because of the lack of industrial support, i.e. nobody can make money by having a better abstract math computation system. Following is the list of current market leaders and their open-source competitors/clones:

| Proprietary software | Speciality | Open source alternative | Equivalent/complementary Python libraries |
|----------|----------| ---------- | --------- |
|SAS/SPSS | Statistical computations | RStudio | statsmodels (NumPy + SciPy + pandas + Patsy + ...)|
|MATLAB | Numerical computations (applied maths) | GNU Octave/Scilab | SciPy + NumPy + Matplotlib |
|Mathematica/Maple ([Macsyma](https://en.wikipedia.org/wiki/Macsyma))| Symbolic computations (UG level maths) | Maxima  | SymPy (NumPy + Matplotlib + mpmath + ...)|
|Magma | [Structural computations](http://magma.maths.usyd.edu.au/magma/overview/2/19/1/#subsection_1_1) (structures from algebra, algebraic geometry and  finite incidence geometry are included) | SageMath (FLINT + PARI/GP + GAP + Singular + ...) | ?? |

I must point out that RStudio is the only open source alternative which has been able to overtake the proprietary software, mainly because [statistical computatiuons can help you make money](https://gkorpal.github.io/files/bp.pdf). Moreover, though the [Anaconda distribution](https://www.anaconda.com/products/individual) has become the standard open-source alternative to all properitary computational softwares, there still isn't any Python library for "structural computations" (Galois representations, isomorphisms, counting points on varieties, etc.). I believe that this is because SageMath's [motto](https://gkorpal.github.io/files/icms_2010.pdf) "building the car instead of reinventing the wheel" turned it into a bloatware since they [integrated other well developed open source programs](https://www.sagemath.org/links-components.html) like R, SymPy and Maxima using Python, instead of just building the Python libraries (like [CyPari2](https://github.com/sagemath/cypari2)) which would act as an [alternative to Magma](https://wiki.sagemath.org/magma), which was [the original goal](https://gkorpal.github.io/files/focm11.pdf). To overcome this [failure](https://sagemath.blogspot.com/2014/08/what-is-sagemathcloud-lets-clear-some.html), SageMath evolved into cloud based subscription service called [CoCalc](https://cocalc.com/index.html) to generate revenue for funding the massive project. Howevever, the main contributions seem to be coming from the developments related to the [LMFDB project](https://www.lmfdb.org/acknowledgment). 

# Mix and match

Open source softwares have been a life saver for students in countries like India, where our universities couldn't afford these proprietary softwares. I learned numerical analysis on GNU Octave and number theory on SageMath.

## General-purpose programming language (open-source)

I would recommend learning Python since it gives you access to all the Python libraries mentioned above. Moreover, SageMath closely follows Python syntax. We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[Python3](https://fedoralovespython.org/) |`python3`|
|[SymPy*](https://developer.fedoraproject.org/tech/languages/python/scipy.html) | `python3-sympy`|
|[CyPARI2](https://pari.math.u-bordeaux.fr/Events/PARI2019/talks/jeroen.html) | `python3-cypari2`|

\*Note that Fedora will automatically install the required dependecies like `mpmath`, `Cython`, `matplotlib` etc.

If you want GUI version of Python development environment then can get [IDLE](https://docs.python.org/3/library/idle.html) by installing the package `python3-idle`. Once you finish learning basics using the free ["Hands-on Python Tutorial" by Andrew N. Harrington](http://anh.cs.luc.edu/python/hands-on/3.1/) or the [tutorial available in the official documentation](https://docs.python.org/3/tutorial/), you will be ready to start using Python for solving math problems.

### SymPy

http://www.math.umbc.edu/~campbell/Computers/Python/numbthy.html

https://docs.sympy.org/latest/modules/ntheory.html

https://docs.sympy.org/latest/modules/polys/agca.html

http://illustratedtheoryofnumbers.com/prog.html

http://math.gordon.edu/ntic/

https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/index.html
https://www.johannes-bauer.com/compsci/ecc/

https://blog.christianperone.com/2010/02/riemann-zeta-function-visualizations-with-python/


### CyPARI2
 
online textbooks

http://math.gordon.edu/ntic/
http://linear.pugetsound.edu/
http://abstract.pugetsound.edu/
http://linear.ups.edu/eagts/eagts.html
https://pretextbook.org/catalog.html

## Domain-specific programming language (proprietary)

Since open source alternative is not sufficient, it would be a good idea to also learn Magma.

https://stackoverflow.com/questions/14030306/lib-ld-linux-so-2-bad-elf-interpreter-no-such-file-or-directory
https://unix.stackexchange.com/questions/75054/ldd-tells-me-my-app-is-not-a-dynamic-executable
https://stackoverflow.com/questions/3949161/no-such-file-or-directory-but-it-exists
