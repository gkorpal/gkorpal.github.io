---
layout: archive
title: "Pencil-paper safe cryptography"
permalink: /pencil/
author_profile: true
redirect_from:
  - /jotting/pencil
  
---

Here we discuss the cryptosystems which played an important role in various battles and the world wars. These systems were considered secure against humans with only pencil and paper.

To get started, I would recommend the following:

| S. No. | Resource |
|--------|----------|
|1 | [Enigma Cryptanalysis](https://gkorpal.github.io/files/summer2015-enigma_cryptanalysis-gaurish.pdf) - Gaurish Korpal (AUD, July 2015)|
|2 | The code book : how to make it, break it, hack it, crack it - Simon Singh (Delacorte Press, 2002)|
|3 | [Lectures on Cryptography: Classical ciphers](https://shrek.unideb.hu/~tengely/crypto/section-2.html) - Szabolcs Tengely (Debrecen, 2020)|
|4 | Introduction to Cryptography with Open-Source Software (first three chapters) - A. McAndrew (CRC Press, 2011)|
|5 | [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf) (first three chapters) - David R. Kohel (July 2008)|
|6 | [Classical Cryptosystems](https://doc.sagemath.org/html/en/reference/cryptography/sage/crypto/classical.html) - David R. Kohel and Minh Van Nguyen (SageMath reference manual, 2007--08)|
|7 | [Sage Interactions - Cryptography](https://wiki.sagemath.org/interact/cryptography) - A. Feaver et al. (SageMath Wiki, August 2019)|
|8 | [pycipher: classical ciphers implemented in Python](https://github.com/jameslyons/pycipher) - J. Lyons et al.|

{% include base_path %}


{% for post in site.pencil %}
  {% include archive-single.html %}
{% endfor %}
