---
title: 'Cross Diagonal Cover - V'
date: 2016-05-09
permalink: /posts/2016/05/cross-diagonal-cover-V/
tags:
  - problem-solving
  - my research
  - algorithm
  - doodling
  - coloring
  - counting
  - python
  - script
  - graph theory
  - sagemath
  - combinatorics
---

This has been an exciting week! <a href="http://www.iitg.ernet.in/pati/" target="_blank">Prof. Sukanta Pati</a> proved an interesting theorem that enables us to get decomposition of $2m-1\times n$ grids into simpler grids, hence simplifying counting to large extent (note that $m=n$ is also allowed). It enables us to surpass the difficulty posed by "more than two crosses in one square", thus supporting the idea of colouring (i.e. not giving importance to two crosses in a square).

<blockquote>Given $m\times n$ grid which has consisting of $m$ rows and $n$ columns such that the terminating corner square lie in $m^{th}$ row. Let the number of covered squares in $m\times n$ grid be $C(m,n)$ . Then for $2m-1\times n$ grid we have $C(2m-1, n)= 2C(m,n)-\beta(m,n)$ where $\beta(m,n)$ is the number of covered squares in $m^{th}$ row of $m\times n$ grid. </blockquote>

Instead of giving its proof, I will give an  example when $m=5, n=10$.

<figure>
  <img src="/images/new-doc-26_1.jpg" alt="my alt text" style="width:600px;height:500px;"/>
  <figcaption>I omitted the repetitions of crosses (x) since the number of x in each square doesn’t matter. Note that if we reflect 5x10 about the middle of 5th row we will get 9x10.</figcaption>
</figure>

Here, $C(5,10) = 25$ and $C(9,10) = 2\times 25 - 5 = 45$. Using this example you can easily prove the generalized statement by exploiting the bilateral symmetry of grid and crosses (x) about the dotted line.

Though I suspected that the least common multiple of $m-1, n-1$ determine the number of steps my algorithm evaluates, <a href="https://www.facebook.com/iampritamlaskar" target="_blank">Pritam Laskar</a>  found the exact formula.

<blockquote>Given a $m\times n$ grid, the Cross Diagonal Cover algorithm terminates after $lcm(m-1, n-1) + 1$  steps.</blockquote>

For proof, follow the arguments of <a href="https://en.gravatar.com/grant93jr" target="_blank">grant93jr</a> in his/her <a href="https://gkorpal.github.io/posts/2016/04/cross-diagonal-cover-III/" target="_blank">comment</a> (he/she mistakenly called their lcm to be their gcd).

Using the SageMath Program, about which I wrote in <a href="https://gkorpal.github.io/posts/2016/05/cross-diagonal-cover-IV/" target="_blank">previous post</a>, I am pretty sure that $\gcd(m,n)$ always divides the number of filled squares. So, now the question is

<blockquote>Why the greatest common divisor of m and n always divides the number of filled squares?</blockquote>
 
