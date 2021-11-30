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
3. 25th IAS Program for Women and Mathematics - [Mathematics of Modern Cryptography](https://www.ias.edu/math/wam/2018) by [Toni Bluher, Kristin Lauter and Jill Pipher](https://youtube.com/playlist?list=PLdDZb3TwJPZ7MPcSPF2Qaqo6azr0VYOK2)
4. MasterMath 2020 (Dutch Master’s Degree Programme in Mathematics) - [Post-quantum cryptography](https://hyperelliptic.org/tanja/teaching/pqcrypto21/) by [Tanja Lange](https://www.youtube.com/channel/UCatHl2XgG1S3Vw4KD8IFnPQ)
5. PBS Infinite Series - [Quantum Computing and Cryptography](https://www.youtube.com/playlist?list=PLa6IE8XPP_gnot4uwqn7BeRJoZcaEsG1D) by [Kelsey Houston-Edwards](https://www.kelseyhoustonedwards.com/video)
6. USF Center for Cryptographic Research - [Quantum Algorithms and Complexity](https://www.usf-crypto.org/mat-4930/) by [Jean-Francois Biasse](https://www.youtube.com/playlist?list=PLasTV9KvJPBusFVpkCVh-W4dYyB9aNkay)
7. CMU Graduate Course 15-859BB (Fall 2018) - [Quantum Computation and Information](https://www.cs.cmu.edu/~odonnell/quantum18/) by [Ryan O'Donnell](https://www.youtube.com/c/RyanODonnellTeaching)
8. Simons Institute for the Theory of Computing - [Workshop on Quantum Cryptanalysis of Post-Quantum Cryptography](https://simons.berkeley.edu/workshops/lattices2020-quantum2020-joint) 
9. Latincrypt 2021 - [ASCRYPTO cryptography summer school](https://www.urosario.edu.co/ascrypto/home/)
10. ANTS 2020 - [Graduate Summer School](https://www.youtube.com/channel/UCuYEpA-S-3wR5lQgkpe-wUw)
11. Post-quantum cryptography (PQCrypto): [https://pqcrypto.org/](https://pqcrypto.org/)

{% include base_path %}


{% for post in site.quantum %}
  {% include archive-single.html %}
{% endfor %}
