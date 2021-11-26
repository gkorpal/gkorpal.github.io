---
layout: archive
title: "Quantum safe cryptography"
permalink: /quantum/
author_profile: true
redirect_from:
  - /jotting/quantum
  
---

Post-quantum cryptography which exploits the limitations of quantum computers.

### References
1. J. Hoffstein, J. Pipher, and J. H. Silverman, An Introduction to Mathematical Cryptography, Springer.
2. S. Galbraith, Mathematics of Public Key Cryptography, CUP. ([version 2.0](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html))
3. 25th IAS Program for Women and Mathematics - [Mathematics of Modern Cryptography](https://www.ias.edu/math/wam/2018)
4. MasterMath 2020 (Dutch Master’s Degree Programme in Mathematics) - [Post-quantum cryptography](https://hyperelliptic.org/tanja/teaching/pqcrypto21/)
5. USF Center for Cryptographic Research - [Quantum Algorithms and Complexity](https://www.usf-crypto.org/mat-4930/)
6. Simons Institute for the Theory of Computing - [Workshop on Quantum Cryptanalysis of Post-Quantum Cryptography](https://simons.berkeley.edu/workshops/lattices2020-quantum2020-joint) 
7. Latincrypt 2021 - [ASCRYPTO cryptography summer school](https://www.urosario.edu.co/ascrypto/home/)
8. Post-quantum cryptography (PQCrypto): [https://pqcrypto.org/](https://pqcrypto.org/)

{% include base_path %}


{% for post in site.quantum %}
  {% include archive-single.html %}
{% endfor %}
