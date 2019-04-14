---
title: 'Cross Diagonal Cover - II'
date: 2016-04-19
permalink: /posts/2016/04/cross-diagonal-cover-II/
tags:
  - problem-solving
  - my research
  - algorithm
  - doodling
  - conjecture
  - counting
---

I will continue the <a href="https://gkorpal.github.io/posts/2016/04/cross-diagonal-cover-I/" target="_blank">previous post</a>. Now the question to  be answered is that:

<blockquote>What percentage (or how many) of given $m\times n$ grid can be covered by following Cross Diagonal Cover Algorithm?</blockquote>

I did some calculations, for example:

<div style="width:image width px; font-size:80%; text-align:center;"><img src="/images/new-doc-16_11.jpg" style="padding-bottom:0.5em;"/> </div>

As per my calculations, I have following conjecture:

<blockquote>The following 3 cases are possible:
<ol>
	<li>If $m = n$, then $m$ squares will be covered.</li>
	<li>If $m>n$ and both $m,n$ are odd, then $m$ squares will be covered.</li>
	<li>If at least one of $m,n$ is even then $\frac{mn}{2}$ squares will be covered.</li>
</ol>
</blockquote>

As you can see that Case - 1 is quite trivial. I tried to prove other two cases for one week, but failed, so decided to post it as conjecture.
