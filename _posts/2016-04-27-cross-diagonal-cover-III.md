---
title: 'Cross Diagonal Cover - III'
date: 2016-04-27
permalink: /posts/2016/04/cross-diagonal-cover-III/
tags:
  - problem-solving
  - my research
  - algorithm
  - doodling
  - coloring
  - counting
---

I found many counterexamples to my <a href="https://gkorpal.github.io/posts/2016/04/cross-diagonal-cover-II/" target="_blank">conjecture</a>, like
<ul>
	<li>for <span style="text-decoration:underline;">Case 2</span> in 7 by 5 grid we have 12, 11 by 5 grid we have 19 and 15 by 5 grid we have 26 filled squares</li>
	<li>for <span style="text-decoration:underline;">Case 3</span> in 4 by 10 grid we have 10 filled squares</li>
</ul>
Also, <a href="https://en.gravatar.com/grant93jr" target="_blank">grant93jr </a>  made the following comment:

<img src="/images/grant.png" alt="">

Therefore (s)he proved the follwing statement:

<blockquote>Given $m>n$, whenever $n-1$ divides $m-1$ we have $m$ filled squares.</blockquote>

Examples of such grids are: 3 by 5, 4 by 7, 4 by 10, ....

In this comment <a href="https://en.gravatar.com/grant93jr" target="_blank">grant93jr </a> also suggested that the algorithm terminates after $k(m-1) = l(n-1)$ steps where $k, l$ are some natural numbers. It is certainly true, but I haven't been able to use this idea for counting number of filled squares when $n-1$ does not divide $m-1$ since in that case some squares are filled twice.

There is another unexplained observation:

<blockquote>Why no filled square has more than 2 crosses?</blockquote>

Frustrated by so many unanswered questions I started colouring squares, so that number of times I visited a square is not visible. Since I really don't care about how many times I visited  given square while counting the number of filled squares this may help in understanding the underlying symmetry.


<figure>
  <img src="/images/new-doc-21_1.jpg" alt="my alt text" style="width:400px;height:800px;"/>
  <figcaption>Replacing cross (x) by any colour and applying Cross Diagonal Cover Algorithm.</figcaption>
</figure>

After observing above diagrams I suspect that my algorithm leads to a non-deterministic <i>cellular automata</i>.

So, the question which still remains to be answered is:

<blockquote>How many filled squares are there when  $m>n$ and $n-1$ does not divide $m-1$ ?</blockquote>

Examples of such grids are: 7 by 5, 11 by 5, 15 by 5 ... 

