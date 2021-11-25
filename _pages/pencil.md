---
layout: archive
title: "Pencil-paper safe cryptography"
permalink: /pencil/
author_profile: true
redirect_from:
  - /jotting/pencil
  
---

Classical cryptosystems which played an important role in various battles and the world wars.

### References
1. G. Korpal, [Enigma Cryptanalysis](https://gkorpal.github.io/files/summer2015-enigma_cryptanalysis-gaurish.pdf), July 2015.
2. S. Tengely, [Lectures on Cryptography](http://shrek.unideb.hu/~tengely/crypto/webwork-mini.html), University of Debrecen, 2020.
3. A. McAndrew, Introduction to Cryptography with Open-Source Software, CRC Press, 2011.
4. David R. Kohel, [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf), July 2008.
5. David R. Kohel and Minh Van Nguyen, [Classical Cryptosystems](https://doc.sagemath.org/html/en/reference/cryptography/sage/crypto/classical.html), SageMath reference manual, 2007--08.
6. A. Feaver et. al., [Sage Interactions - Cryptography](https://wiki.sagemath.org/interact/cryptography), SageMath Wiki, August 2019.
7. J. Lyons et. al., [pycipher](https://github.com/jameslyons/pycipher), classical ciphers implemented in Python.

{% include base_path %}


{% for post in site.pencil %}
  {% include archive-single.html %}
{% endfor %}
