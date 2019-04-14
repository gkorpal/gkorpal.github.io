---
title: 'Cross Diagonal Cover - I'
date: 2016-04-12
permalink: /posts/2016/04/cross-diagonal-cover-I/
tags:
  - problem-solving
  - my research
  - algorithm
  - doodling
---

While doodling in my college classes, I designed an algorithm which I called <span style="text-decoration:underline;">Cross Diagonal Cover Algorithm</span>:

<blockquote>I have a $m\times n$ rectangle divided into unit squares. I start by placing a x (cross) in leftmost corner. Every time I visit a square in diagonal direction I place a  x in the squares till I reach any boundary of rectangle, from where I switch to adjacent diagonal.</blockquote>

<div style="width:image width px; font-size:80%; text-align:center;"><img src="/images/new-doc-17_1.jpg" style="padding-bottom:0.5em;"/> Illustrating the algorithm… Follow the arrow numbers to fill the grid.</div>

Please note that it doesn't matter that how many x (cross) are there in each square. The number of x (cross) in each square just signify number of times I visited that square while executing the algorithm.

Then I asked myself the following question:

<blockquote>Can I cover whole grid with at least one x in each unit square?</blockquote>

The answer to my above question is <b>NO</b>! The proof is pretty easy.

<i>If $m=n$ then it's trivial that I can't cover the whole grid with x since I will  be tracing the main diagonal again and again. </i>

<i>Moreover, the key observation here is that I will be stuck in loop (which can't cover whole grid) whenever I reach another corner of the grid since it supports only one diagonal. Since I want to cover whole grid I must visit all the corners but they are dead ends! </i>

<i>Quod Erat Demonstrandum.</i>

Any references about this idea from literature would be appreciated. I am working on a better question on "Cross Diagonal Cover Algorithm", which I will discuss in next post.
