---
title: 'Richert Theorem'
date: 2018-12-28
permalink: /posts/2018/12/richert-theorem/
tags:
  - problem solving
  - bertrand's postulate
  - chebyshev
  - Erdos
  - prime numbers
  - richert
  - sierpinski
  - sum of primes
  - turner
---

In 1852, Chebyshev proved the Bertrand's postulate:
<blockquote>For any integer $n>1$, there always exists at least one prime number $p$ with $< p < 2n$.</blockquote>
You can find Erdős' elementary proof <a href="https://gaurish4math.files.wordpress.com/2014/12/erdos.pdf" target="_blank" rel="noopener">here</a>. In this post I would like to discuss an application of this fantastic result, discovered by <a href="https://en.wikipedia.org/wiki/Hans-Egon_Richert" target="_blank" rel="noopener">Hans-Egon Richert</a> in 1948:
<blockquote>Every integer $ n\geq 7$ can be expressed as a sum of distinct primes.</blockquote>
There are several proofs available in literature, but we will follow the short proof given by Richert himself (english translation has been taken from <a href="https://math.stackexchange.com/a/1382818/214604" target="_blank" rel="noopener">here</a> and <a href="https://math.stackexchange.com/a/1382840/214604" target="_blank" rel="noopener">here</a>):

Consider the set of prime integers $ \{p_1, p_2,p_3,\ldots\}$ where $ p_1=2, p_2=3, p_3=5,\ldots $. By Bertrand's postulate we know that $ \boxed{p_i < p_{i+1} < 2p_i }$.

Next, we observe that, any integer between 7 and 19 can be written as a sum of distinct first 5 prime integers $ \{2,3,5,7,11\}$:

<span style="color:#800000;">7 = 5+2</span>; <span style="color:#008000;">8 = 5+3</span>; <span style="color:#800000;">9 = 7+2</span>; <span style="color:#008000;">10 = 5+3+2</span>; <span style="color:#800000;">11 = 11</span>; <span style="color:#008000;">12 = 7+5</span>; <span style="color:#800000;">13 = 11+2</span>; <span style="color:#008000;">14 = 7+5+2</span>; <span style="color:#800000;">15 = 7+5+3</span>; <span style="color:#008000;">16 = 11+5</span>; <span style="color:#800000;">17 = 7+5+3+2</span>; <span style="color:#008000;">18 = 11+7</span>; <span style="color:#800000;">19 = 11+5+3</span>

Hence we fix $ a=7-1=6$, $ b=19-a=13$, and $ k=5$ to conclude that $ \boxed{b \geq p_{k+1}}$.

Let, $ S_i = \{a+1,a+2,\ldots, a+p_{i+1}\}=\{7,8,\ldots, 6+p_{i+1}\}$. Then by the above observation we know that the elements of $ S_k = S_5 = \{7,8,\ldots, 19\}$ are the sum of distinct first $ k=5$ prime integers.
Moreover, if the elements of $ S_i$ can be written as the sum of distinct first $ i$ prime integers, then the elements of $ S_{i+1}$ can also be written as the sum of distinct first $ i+1$ prime integers since
<p style="text-align:center;">$ S_{i+1}\subset S_i \cup \{m + p_{i+1}: m\in S_{i}\}$</p>
as a consequence of $ 2p_{i+1} \geq p_{i+2}$.

Hence inductively the result follows by considering $ \bigcup_{i\ge k} S_i$, which contains all integers greater than $ a=6$, and contains only elements which are distinct sums of primes.

<hr />

<strong>Exercise:</strong> <em>Use Bertrand's postulate to</em> g<em>eneralize the statement <a href="https://gaurish4math.wordpress.com/2017/06/25/finite-sum-divisibility/" target="_blank" rel="noopener">proved earlier:</a> </em>If $ n>1$ and $ k$  are natural numbers , then the sum
<p style="text-align:center;">$ \displaystyle{\frac{1}{n}+ \frac{1}{n+1} + \ldots + \frac{1}{n+k}}$</p>
cannot be an integer.

[HINT: Look at the <a href="https://gaurish4math.wordpress.com/2017/06/25/finite-sum-divisibility/#comment-534" target="_blank" rel="noopener">comment by Dan</a> in the earlier post.]

<hr />

<strong>References:</strong>
[0] Turner, C. (2015) <a href="https://math.stackexchange.com/a/1382818/214604" target="_blank" rel="noopener">A theorem of Richert</a>. Math.SE profile: https://math.stackexchange.com/users/37268/sharkos

[1] Richert, H. E. (1950). <a href="https://rdcu.be/beceV" target="_blank" rel="noopener">Über Zerfällungen in ungleiche Primzahlen</a>. (German). Mathematische Zeitschrift 52, pp. 342-343.  https://doi.org/10.1007/BF02230699

[2] Sierpiński,W. (1988). <a href="https://www.elsevier.com/books/elementary-theory-of-numbers/sierpinski/978-0-444-86662-2" target="_blank" rel="noopener">Elementary theory of numbers</a>. North-Holland Mathematical Library 31, pp. 137-153.
