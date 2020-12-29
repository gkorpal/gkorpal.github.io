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

| Proprietary software | Speciality | Open source alternative | Equivalent/complementary [Python libraries](https://wiki.python.org/moin/Libraries) |
|----------|----------| ---------- | --------- |
|SAS/SPSS | Statistical computations | RStudio | statsmodels (NumPy + SciPy + pandas + Patsy + Matplotlib +...)|
|MATLAB | Numerical computations (applied maths) | GNU Octave/Scilab | SciPy (NumPy + Matplotlib + ...) |
|Mathematica/Maple ([Macsyma](https://en.wikipedia.org/wiki/Macsyma))| Symbolic computations (UG level maths) | Maxima  | SymPy (NumPy + Matplotlib + mpmath + ...)|
|Magma | [Structural computations](http://magma.maths.usyd.edu.au/magma/overview/2/19/1/#subsection_1_1) (structures from algebra, algebraic geometry and  finite incidence geometry are included) | SageMath (FLINT + PARI/GP + GAP + Singular + ...) | CyPari2 + ?? |

For a more up-to-date information, have a look at these [ICMS proceedings](https://link.springer.com/conference/icms).

I must point out that RStudio is the only open source alternative which has been able to overtake the proprietary alternatives, mainly because [statistical computatiuons can help you make money](https://gkorpal.github.io/files/bp.pdf). Moreover, though the [Anaconda distribution](https://www.anaconda.com/products/individual) has become the standard open-source alternative to all properitary computational softwares, there still isn't any Python library for "structural computations" (Galois representations, isomorphisms, counting points on varieties, etc.). I believe that this is because SageMath's [motto](https://gkorpal.github.io/files/icms_2010.pdf) "building the car instead of reinventing the wheel" turned it into a bloatware since they [integrated other well developed open source programs](https://www.sagemath.org/links-components.html) like R, SymPy and Maxima using Python, instead of just building the Python libraries (like [CyPari2](https://github.com/sagemath/cypari2)) which would act as an [alternative to Magma](https://wiki.sagemath.org/magma), which was [the original goal](https://gkorpal.github.io/files/focm11.pdf). To overcome this [failure](https://sagemath.blogspot.com/2014/08/what-is-sagemathcloud-lets-clear-some.html), SageMath evolved into cloud based subscription service called [CoCalc](https://cocalc.com/index.html) to generate revenue for funding the massive project. Howevever, the main contributions seem to be coming from the developments related to the [LMFDB project](https://www.lmfdb.org/acknowledgment). 

# Mix and match

Open source softwares have been a life saver for students in countries like India, where our universities couldn't afford the proprietary softwares. I myself learned numerical analysis on [GNU Octave](https://www.gnu.org/software/octave/) and number theory on [SageMath](https://www.sagemath.org/).

## Python: General-purpose programming language (open-source)

When I was an undergraduate student, C++ was the langauge promoted for scientific computations. In fact, there are many C/C++ libraries for scientific computations, like [NTL](https://libntl.org), [FLINT](http://www.flintlib.org/), [eclib](http://homepages.warwick.ac.uk/staff/J.E.Cremona/mwrank/), [gf2x](https://gitlab.inria.fr/gf2x/gf2x), [Givaro](https://casys.gricad-pages.univ-grenoble-alpes.fr/givaro/), [GMP](https://gmplib.org/), [GNU MPFR](https://www.mpfr.org/), [GNU MPC](http://www.multiprecision.org/mpc/), [ARB](https://arblib.org/), [CMH](https://gitlab.inria.fr/cmh/cmh#cmh-computation-of-genus-2-class-polynomials), [LinBox](https://linalg.org/), [PARI](http://pari.math.u-bordeaux.fr/), [Symmetrica](http://www.algorithm.uni-bayreuth.de/en/research/SYMMETRICA/), [zn_poly](https://web.maths.unsw.edu.au/~davidharvey/code/zn_poly/), and [m4ri](https://bitbucket.org/malb/m4ri/). However, with the advent of Cython (not to be confused with CPython, which is the original [Python implementation](https://wiki.python.org/moin/PythonImplementations)), Python has become the new langauge for scientific computations. In fact, all these C/C++ libraries can now be [accessed via SageMath](https://www.sagemath.org/links-components.html) using Python-based syntax. 

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[Python3](https://fedoralovespython.org/) |`python3`|
|[SymPy*](https://developer.fedoraproject.org/tech/languages/python/scipy.html) | `python3-sympy`|
|[CyPARI2](https://pari.math.u-bordeaux.fr/Events/PARI2019/talks/jeroen.html) | `python3-cypari2`|

\*Note that Fedora will automatically install the required dependecies like `mpmath`, `Cython`, `matplotlib` etc.

If you want GUI version of Python development environment then can get [IDLE](https://docs.python.org/3/library/idle.html) by installing the package `python3-idle`. Once you finish learning basics using the free ["Hands-on Python Tutorial" by Andrew N. Harrington](http://anh.cs.luc.edu/python/hands-on/3.1/) or the [tutorial available in the official documentation](https://docs.python.org/3/tutorial/), you will be ready to start using Python for solving math problems.

We will use Vim as the text editor for writing [Python scripts](https://docs.python.org/3/tutorial/modules.html). Note that [we don't need](https://unix.stackexchange.com/a/27795/420307) to add a file extension, however for proper syntax highlighting we will use the file extension `.py`. Therefore, it would be helpful to install the `python-mode` plugin ([instructions](https://github.com/python-mode/python-mode)). Following are some the key mappings for some of the `python-mode` commands ([documentation](https://github.com/python-mode/python-mode/blob/develop/doc/pymode.txt)):

| Key mapping | Python-mode command  (normal mode)| Output |
|----------|----------|----------|
| `\\r` | :PymodeRun | Run current code script buffer or selection |
| (<kbd>Ctrl</kbd>+<kbd>w</kbd>) + <kbd>z</kbd> | :pclose | Close the code preview window ([not in doc](https://stackoverflow.com/a/52464433/))|
| <kbd>Shift</kbd> + <kbd>k</kbd> | :PymodeDoc | Show documentation for current word|
| <kbd>Ctrl</kbd> + <kbd>p</kbd> | Usual Vim key binding | Auto-complete a word that has already been typed once in the document|

Note that the text-wrap is disabled by default, with the maximum line length of 79 characters. Moreover, it uses `pylint` to check code at every save. I couldn't figureout how to use code completion via `rope`.

### Examples

We will take some examples from SageMath and solve them using Python libraries:

-  Plotting elliptic curves over affine plane

    - SageMath code and output
  
```` sage
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


- Plotting elliptic curve modulo prime

    - SageMath code and output
    
    ```` sage
    E=EllipticCurve(GF(1021),[0,-1,-1,0,0])
    A=E.plot()
    show(A)
    A.save('v1.pdf')
    ````
    
    ![ec2](https://gkorpal.github.io/images/sage2.png)
    
 - Comparing the prime counting functions
 
    - SageMath code and output
    
    ```` sage
    P = plot(Li(x), (x,2,10000), linestyle="--", thickness=2, rgbcolor=(0,0,0), legend_label='$\\mathrm{Li}(x)$')
    Q = plot(prime_pi(x), (x,2,10000),thickness=2, rgbcolor=(0,0,0), legend_label='$\\pi(x)$')
    R = plot(x/log(x), (x,2,10000), linestyle=":", thickness=3, rgbcolor=(0,0,0), legend_label='$x/\\log(x)$')
    (P+Q+R)
    ````
    
    ![prime](https://gkorpal.github.io/images/sage5.png)
    
- Plotting Riemann zeta function for real inputs (trivial zeros)

    - SageMath code and output
    
    ```` sage
    p=plot(zeta(x), (x,-13,-1), legend_label='$\\zeta(x)$')
    show(p)
    ````
    
    ![ec3](https://gkorpal.github.io/images/sage3.png)
    
- Plotting  the  real  and  imaginary  parts  of  the  Riemann  zeta  function $\zeta(1/2 + it)$  for $0 < t < 30$

    - SageMath code and output
    
    ````sage
    i = CDF.gen()
    v = [zeta(0.5 + n/10 * i) for n in range(300)]
    L = [(z.real(), z.imag()) for z in v]
    line(L)
    ````
    
    ![ec4](https://gkorpal.github.io/images/sage4.png)

- Comparing the argument and absolute values of Riemann zeta function $\zeta(1/2 + it)$  for $0 \leq  t \leq 50$

    - SageMath code and output
    
    ````sage
    i = CDF.0
    p1 = plot(lambda t:  arg(zeta(0.5+t*i)), 1, 50,linestyle="--", rgbcolor=(0,0,0), legend_label='$\\mathrm{arg}(\\zeta(0.5+it))$')
    p2 = plot(lambda t:  abs(zeta(0.5+t*i)), 1, 50, rgbcolor=(0,0,0), legend_label='$|\\zeta(0.5+it)|$')
    p1+p2
    ````
    ![prime](https://gkorpal.github.io/images/sage6a.png)

- Plotting complex valued functions

    - SageMath code and output
    
    ```` sage
    complex_plot(x^4-1,(-5,5),(-5,5))
    ````
   ![prime](https://gkorpal.github.io/images/sage7.png)

    
- Ideal factorization

    - SageMath code and output
    
    ````sage
    K.<a>=NumberField(x^3-19)
    I = K.ideal(3)
    F = I.factor()
    F
    ````
    
    ````
    (Fractional ideal (3, 1/3*a^2 + 1/3*a + 1/3))^2 * (Fractional ideal (3, 1/3*a^2 + 1/3*a - 2/3))
    ````
    
    
https://blog.christianperone.com/2010/02/riemann-zeta-function-visualizations-with-python/


https://cypari2.readthedocs.io/en/latest/pari_instance.html

<!--- http://math.gordon.edu/ntic/ http://linear.pugetsound.edu/ http://abstract.pugetsound.edu/ http://linear.ups.edu/eagts/eagts.html https://pretextbook.org/catalog.html --->


http://www.math.umbc.edu/~campbell/Computers/Python/numbthy.html

https://docs.sympy.org/latest/modules/ntheory.html

https://docs.sympy.org/latest/modules/polys/agca.html

http://illustratedtheoryofnumbers.com/prog.html

http://math.gordon.edu/ntic/

https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/index.html
https://www.johannes-bauer.com/compsci/ecc/

Write your own script: https://arxiv.org/abs/2004.09046

## Magma: Domain-specific programming language (proprietary)

There exist individual C/C++ libraries, like [FLINT](http://www.flintlib.org/) and [m4ri](https://bitbucket.org/malb/m4ri/wiki/Performance), which are much more efficient than Magma. In fact, Magma itself uses some of the C/C++ libraries like  [ATLAS](http://math-atlas.sourceforge.net/), [GMP](https://gmplib.org/), [GMP-ECM](https://gforge.inria.fr/projects/ecm/), [MPC](http://www.multiprecision.org/mpc/), and [MPFR](http://www.mpfr.org/). However, there aren't enough libraries available to help SageMath replace Magma completely. In fact, as per SageMath's [October 2008 Bordeaux meeting](https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/introduction.html#the-sage-pari-magma-ecosystem):

> Any mathematician who is serious about doing extensive computational work in algebraic number theory and arithmetic geometry is strongly urged to become familiar with all three systems [Sage, Pari and Magma], since they all have their pros and cons. Pari is sleek and small, Magma has much unique functionality for computations in arithmetic geometry, and Sage has a wide range of functionality in most areas of mathematics, a large developer community, and much unique new code.

In the USA, because of the [Simons Foundation Agreement](http://magma.maths.usyd.edu.au/magma/simons_details), you can get access to Magma for free by contacting your department's IT support staff. You should be able to access its full-version on your department's computer clusters and student-version on your personal computer ([installation steps](http://magma.maths.usyd.edu.au/magma/faq/install)). Note that the student-version is available only for the outdated [32-bit architecture](http://magma.maths.usyd.edu.au/magma/download/all/), therefore you might also need to [install additonal packages](https://unix.stackexchange.com/q/75054/) like `glibc.i686` in Fedora ([details](https://stackoverflow.com/a/25269017/)) or `ia32-libs-multiarch` in Ubuntu ([details](https://stackoverflow.com/a/3949268/)). 


We will use Vim as the text editor for writing Magma scripts. Note that, just like for Python scripts, we don't need to add any specific filename extensions to the text files in order to be able to "load them" in Magma ([details](https://gkorpal.github.io/files/magma.pdf)). However, one can use filename extension `.m` to get Objective-C syntax highlighting (`objc.vim`) and to be consistent with the extension used for magma package files ([details](https://gkorpal.github.io/files/msri_magma.pdf)). Moreover, we can run the code without having to leave the text editor by adding the following to `.vimrc` file ([source](https://stackoverflow.com/questions/3166413/execute-a-script-directly-within-vim-mvim-gvim)):

`````
map <F2> :w<CR>:!magma %<CR> "once you press <F2> in normal mode, it first saves your file and then run the file with magma.
imap <F2> <Esc>:w<CR>:!magma %<CR> "once you press <F2> in insert mode, it first leaves insert mode, then saves the file and then run the file with magma.
`````

https://github.com/petRUShka/vim-magma

http://magma.maths.usyd.edu.au/magma/handbook/text/53


https://stackoverflow.com/questions/14030306/lib-ld-linux-so-2-bad-elf-interpreter-no-such-file-or-directory
https://unix.stackexchange.com/questions/75054/ldd-tells-me-my-app-is-not-a-dynamic-executable
https://stackoverflow.com/questions/3949161/no-such-file-or-directory-but-it-exists

points on elliptic curve
https://doc.sagemath.org/html/en/thematic_tutorials/explicit_methods_in_number_theory/index.html#explicit-methods-in-number-theory


http://brauer.math.harvard.edu/computing/magma/index.html

