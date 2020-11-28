---
layout: single
title:  "Computations in Arithmetic Geometry"
header:
categories: 
  - Jekyll
tags:
  - edge case
---


| Proprietary software | Speciality | Open source alternative | Equivalent/complementary Python libraries |
|----------|----------| ---------- | --------- |
|SAS/SPSS | Statistical computations | RStudio | NumPy + SciPy + Matplotlib + pandas + Statsmodels + Patsy|
|MATLAB | Numerical computations (applied maths) | GNU Octave/Scilab | NumPy + SciPy + Matplotlib |
|Mathematica/Maple ([Macsyma](https://en.wikipedia.org/wiki/Macsyma))| Symbolic computations (UG level maths) | Maxima  | NumPy + Matplotlib + SymPy |
|Magma | [Structural computations](http://magma.maths.usyd.edu.au/magma/overview/2/19/1/#subsection_1_1) (structures from algebra, algebraic geometry and  finite incidence geometry are included) | SageMath (FLINT + PARI/GP + GAP + Singular + ...) | ?? |

However, RStudio is the only open source alternative which has been able to overtake the proprietary software. This is because other alternatives [don't have any industry backing](https://gkorpal.github.io/files/bp.pdf). Moreover, SageMath's [motto](https://gkorpal.github.io/files/icms_2010.pdf) "building the car instead of reinventing the wheel" turned it into a bloatware since they [integrated other well developed open source programs](https://www.sagemath.org/links-components.html) like R, SymPy and Maxima using Python, instead of just building the Python libraries (like [CyPari2](https://github.com/sagemath/cypari2)) which would act as an [alternative to Magma](https://wiki.sagemath.org/magma), which was [the original goal](https://gkorpal.github.io/files/focm11.pdf). To overcome this [organizational failure](https://sagemath.blogspot.com/2014/08/what-is-sagemathcloud-lets-clear-some.html), SageMath has evolved into [CoCalc](https://cocalc.com/index.html) to become more market-friendly and is able to support further development via [LMFDB project](https://www.lmfdb.org/acknowledgment). 

# Python configuration

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[Python3](https://fedoralovespython.org/) |`python3`|
|[SymPy](https://developer.fedoraproject.org/tech/languages/python/scipy.html) | `python3-sympy`|
|[CyPARI2](https://pari.math.u-bordeaux.fr/Events/PARI2019/talks/jeroen.html) | `python3-cypari2`|

If you want GUI version of Python development environment then can get [IDLE](https://docs.python.org/3/library/idle.html) by installing the package `python3-idle`. Once you finish learning basics using the free ["Hands-on Python Tutorial" by Andrew N. Harrington](http://anh.cs.luc.edu/python/hands-on/3.1/) or the [tutorial available in the official documentation](https://docs.python.org/3/tutorial/), you will be ready to start using Python for solving math problems.

# SymPy

http://www.math.umbc.edu/~campbell/Computers/Python/numbthy.html

https://docs.sympy.org/latest/modules/ntheory.html

https://docs.sympy.org/latest/modules/polys/agca.html

http://illustratedtheoryofnumbers.com/prog.html

http://math.gordon.edu/ntic/

https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/index.html
https://www.johannes-bauer.com/compsci/ecc/

## Matplotlib

## NumPy

# CyPARI2
 
online textbooks

http://math.gordon.edu/ntic/
http://linear.pugetsound.edu/
http://abstract.pugetsound.edu/
http://linear.ups.edu/eagts/eagts.html
https://pretextbook.org/catalog.html


