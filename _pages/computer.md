---
layout: archive
title: "Computer safe cryptography"
permalink: /computer/
author_profile: true
redirect_from:
  - /jotting/computer
  
---

Symmetric and public-key cryptography which exploits the limitations of modern computers.

### References
1. J. Katz and Y. Lindell, Introduction to Modern Cryptography, CRC.
2. A. Joux, Algorithmic Cryptanalysis, CRC.
3. J. Hoffstein, J. Pipher, and J. H. Silverman, An Introduction to Mathematical Cryptography, Springer.
4. S. Galbraith, Mathematics of Public Key Cryptography, CUP. ([version 2.0](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html))
5. Eindhoven University of Technology, Bachelor's course: [Intorduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/)
6. Eindhoven University of Technology, Master's course: [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/)
7. USF Center for Cryptographic Research: [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/)
8. Maryland Cybersecurity Center: [Cybersecurity Specialization](https://cyber.umd.edu/education/beyond-umd)
9. Stanford University: [A graduate course in applied cryptography](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/)

{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
