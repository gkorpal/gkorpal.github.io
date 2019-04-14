---
title: 'Spot The Flaw'
date: 2014-10-04
permalink: /posts/2012/08/spot-the-flaw/
tags:
  - problem solving
---

Many of you must have seen numerous examples of such situations where we get an absurd result and have to spot flaw in proof.

A famous one is the "<a href="https://www.math.hmc.edu/funfacts/ffiles/10001.1-8.shtml">algebraic proof of 1=0</a>"

Here I came across a "Calculus based proof of 1=0" in <a href="http://www.amazon.in/gp/product/1895997283/ref=pd_lpo_sbs_dp_ss_1/188-2419432-6341959?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=lpo-top-stripe-1&pf_rd_r=1XX7N9TVGGNWXDS2KAHV&pf_rd_t=201&pf_rd_p=1944687502&pf_rd_i=1895997046"><em>A Mathematical Mosaic</em> </a>which I wanted to share with you.

It is based on "Integration by Parts" formula, which is:

$$ \int f \ dg = fg - \int g \ df \nonumber$$

So, the proof is of this is as follows:

$$ \int \frac{1}{x} dx = \left(\frac{1}{x}\right) x - \int x \ d \left(\frac{1}{x}\right) = 1 - \int x \left(-\frac{1}{x^2}\right) dx = 1 + \int \frac{1}{x}dx \nonumber$$

$$\Rightarrow 0 = 1 \nonumber$$
