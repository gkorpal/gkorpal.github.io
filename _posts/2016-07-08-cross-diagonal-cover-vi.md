---
title: 'Cross Diagonal Cover - VI'
date: 2016-07-08
permalink: /posts/2016/07/cross-diagonal-cover-VI/
tags:
  - problem-solving
  - my research
  - grid
  - matthew scroggs
  - coloring
  - counting
  - proof
  - solution
  - sagemath
  - combinatorics
---
The problem has finally been solved by <a href="http://www.mscroggs.co.uk/" target="_blank" rel="noopener">Matthew Scroggs</a>.

${\text{\# filled squares} = (\mathrm{lcm}(m-1,n-1)+1 )- \frac12\left(\frac{\mathrm{lcm}(m-1,n-1)}{m-1}-1\right)\left(\frac{\mathrm{lcm}(m-1,n-1)}{n-1}-1\right)}$

He and I, independently,  found a counterexample  for the <a href="https://gkorpal.github.io/posts/2016/05/cross-diagonal-cover-V/" target="_blank" rel="noopener">conjecture</a> by replacing lowest common multiple by greatest common factor using the relation: $ab=\mathrm{lcm}(a,b)\gcd(a,b)$.

<blockquote>In 15x5, there are 26 filled squares and gcd(15,5)=5, so 15x5 is a counterexample to the conjecture!</blockquote>

As it turns out, SAGE is giving float(26/5) = 5.0 when I run it inside the program, but return 5.2 when I run it independently. Leading to wrong conjecture.

The <a href="http://www.mscroggs.co.uk/blog/32" target="_blank" rel="noopener">solution</a> is pretty beautiful and  this is the outline:

<blockquote>There are 3 levels of simplifications of the problem:
Original Grid --> Dual Grid --> Mirror Grid --> Inner-point Grid</blockquote>

Counting the "Corners visited twice" (the subtracted term) was something I wasn't able to do. Corners visited was essentially what I called "<a href="https://gkorpal.github.io/posts/2016/05/cross-diagonal-cover-V/" target="_blank" rel="noopener">number of steps needed for algorithm to stop</a>". So, his mirror argument provides a proof without words of that result.
