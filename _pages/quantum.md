---
layout: archive
title: "Quantum safe cryptography"
permalink: /quantum/
author_profile: true
redirect_from:
  - /jotting/quantum
  
---

Here we discuss the cryptosystems which are expected to play an important role in future. These are considered secure against quantum computers. That is, the kind of computers built using quantum physics theories. 

To get started, one can consider the following resources:

| S. No. | Books/lecture notes/video lectures |
| ------ | ---------------------------------- |
|1 | An Introduction to Mathematical Cryptography - Jeffrey Hoffstein et al. (Springer, 2008) |
|2 | [Mathematics of Public Key Cryptography](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html) - Steven D. Galbraith (CUP, Oct 2018)|
|3 | [Mathematics of Modern Cryptography](https://www.ias.edu/math/wam/2018) - Toni Bluher et al. (2018) ([YouTube](https://youtube.com/playlist?list=PLdDZb3TwJPZ7MPcSPF2Qaqo6azr0VYOK2))
|4 | [Post-quantum cryptography](https://hyperelliptic.org/tanja/teaching/pqcrypto21/) - Tanja Lange (TU/e, 2021) |
|5 | [Introduction to mathematical cryptography](https://www.uvm.edu/~cvincen1/pcmi-uss.html) - Christelle Vincent (PCMI, 2022) |
|6 | [Quantum Algorithms and Complexity](https://www.usf-crypto.org/mat-4930/) - Jean-Francois Biasse (USF, 2021) |
|7 | [Quantum Computing and Cryptography](https://www.youtube.com/playlist?list=PLa6IE8XPP_gnot4uwqn7BeRJoZcaEsG1D) by Kelsey Houston-Edwards (PBS, 2017)
|8 | [Workshop on Quantum Cryptanalysis of Post-Quantum Cryptography](https://simons.berkeley.edu/workshops/schedule/14097) - Simons Institute for the Theory of Computing (2020)|
|9 | [ASCRYPTO cryptography summer school](https://www.urosario.edu.co/ascrypto/home/) - Latincrypt 2021|
|10| [Graduate Summer School](https://www.youtube.com/channel/UCuYEpA-S-3wR5lQgkpe-wUw) - ANTS 2020 |

<!----7. CMU Graduate Course 15-859BB (Fall 2018) - [Quantum Computation and Information](https://www.cs.cmu.edu/~odonnell/quantum18/) by [Ryan O'Donnell](https://www.youtube.com/c/RyanODonnellTeaching) ---->

{% include base_path %}


{% for post in site.quantum %}
  {% include archive-single.html %}
{% endfor %}
