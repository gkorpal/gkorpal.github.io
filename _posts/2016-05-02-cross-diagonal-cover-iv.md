---
title: 'Cross Diagonal Cover - IV'
date: 2016-04-27
permalink: /posts/2016/04/cross-diagonal-cover-IV/
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
---
While discussing this problem with <a href="http://www.ramanujanmathsociety.org/people/drshaileshshirali" target="_blank">Dr. Shailesh Shirali</a>, he commented that there has to be a way to phrase the problem in terms of a ray of light being reflected off the walls of the rectangle, bouncing around, proceeding from one corner to some other corner.

The problem in re-stating my problem in "light reflection" form was that reflections must be from center of squares and this is not the way light "actually" reflects from surfaces. But, I clubbed that idea with "graph theory" (directed graphs), which actually answers the first question I asked in my <a href="https://gkorpal.github.io/posts/2016/04/cross-diagonal-cover-III/" target="_blank">previous post</a>:

<blockquote>Why no filled square has more than 2 crosses?</blockquote>

<em>As per my "Cross diagonal cover algorithm" we can't retrace a path and each square has just two diagonals. Hence, if we replace all the squares by their centers then each center is of degree two (i.e. can allow intersection of at most two distinct paths). Hence proving that no filled square can have more than 2 crosses.</em> For example:

<img src="/images/new-doc-22_1.jpg" alt="New Doc 22_1"/>

Now moving to the bigger question of counting the total number of filled squares, there hasn't been much progress yet (even on arriving at a concrete conjecture). But, <a href="http://www.imsc.res.in/~amri/" target="_blank">Prof. Amritanshu Prasad </a>wrote a <a href="http://www.sagemath.org/" target="_blank">SageMath </a> program for my algorithm which enables us to find number of the filled squares for individual cases without actually drawing them! <em>For Example: for m=101 , n=102 grid, there will be 5151 = (101 * 102 )/ 2 filled squares. </em>Pretty cool :)

SageMath is is an open source implementation of mathematics and scientific software based on <a href="https://wiki.python.org/moin/SageMath" target="_blank">Python 2</a>.  Unfortunately, since the SageMath program is essentially a Python script I am <a href="https://en.support.wordpress.com/code/" target="_blank">not allowed to embed </a> it in my Wordpress.com blog. But, motivated by my discussions with <a href="http://www.thebadbyte.com/p/about.html" target="_blank">Ms. Marina Ibrishimova</a>, I tweaked Prof. Prasad's original source-code and added comments (initialized by #) to make it self explanatory.

Here is the SageMath (or Python) code to count the number of filled squares for $2 \leq m\leq n\leq 10$

<pre>
#-----START OF PYTHON FUNCTION FOR CROSS DIAGONAL COVER ALGORITHM-----

def cover(m,n):
#a function to count the number of squares covered in a grid with m rows
#and n columns
    xinc = 1
#we will use this variable to increment (or decrement) the value of
#x-coordinate (row position) by 1 unit after each step
    yinc = 1
#we will use this variable to increment (or decrement) the value of
#y-coordinate (column position) by 1 unit after each step
    pos = [1, 1]
#we are assuming our grid to have at least 2 rows and 2 columns
#and will initialize counting from (1,1) position.
    visited = [[0, 0], [1, 1]]
#since we start from (1,1) position, we implicitly assume to have
#counted (0,0) position.
    while pos != [m-1, 0] and pos != [0, n-1] and pos != [m - 1, n - 1]:
#whenever we reach any corner the algorithm terminates, so need to include
#position of other three corners apart from starting corner in condition.
          if pos[0] in [0, m-1]:
#evaluates to true if x-coordinate of current position is a
#member of the collection [0,m-1]
             xinc = - xinc
#if x-coordinate is either 0 or m-1 then we will switch diagonal
#by switching the sign of xinc
          if pos[1] in [0, n-1]:
#evaluates to true if y-coordinate of current position is a member
#of the collection [0,n-1]
             yinc = -yinc
#if y-coordinate is either 0 or n-1 then we will switch diagonal
#by switching the sign of yinc
          pos[0] += xinc
#update the x-coordinate of new position as x(new) = x(old) + xinc,
# where xinc = 1 or -1.
          pos[1] += yinc
#update the y-coordinate of new position as y(new) = y(old) + yinc,
# where yinc = 1 or -1.
          if not (pos in visited):
#if this new state is not there in visited positions list
             visited.append([pos[0], pos[1]])
#then add this new position to the list of visited positions.
    return visited 

#---------------END OF FUNCTION---------------

#we will write a small code to be able to use above function to find number of
#filled squares for all grids where m,n lie between 1 and 11 (both excluded).

for i in range (2, 11):
#The range() function provides an easy way to construct a list of integers.
#The range() function only does numbers from the first to the last,
#not including the last.
    for j in range(i, 11):
        print i, j, len(cover(i, j))
# len(indata) counts the bytes of data in indata here it
#counts the number of elements is visited list.
</pre>

To run the above code, please copy-paste it in <a href="https://sagecell.sagemath.org/" target="_blank">SageMathCell</a> and click evaluate button. You will get the list displaying m, n and the number of filled squares in each of the grid (with 1<m,n<11).

In case you want to understand above Python function, here is an illustration when m=3 and n=4:

<div style="width:image width px; font-size:80%; text-align:center;"><img src="/images/new-doc-23_1.jpg" style="padding-bottom:0.5em;"/>Note that though (1,1) position is encountered twice but it is added to "visited squares" list only once.</div>

So far I haven't been able to derive a useful interpretation even after getting access to lot of data. I hope to formulate a conjecture soon...
