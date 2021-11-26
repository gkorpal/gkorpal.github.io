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
1. S. Tengely, [Lectures on Cryptography](http://shrek.unideb.hu/~tengely/crypto/webwork-mini.html), University of Debrecen, 2020.
2. D. Kohel, [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf), July 2008.
3. A. McAndrew, Introduction to Cryptography with Open-Source Software, CRC.
4. J. Katz and Y. Lindell, Introduction to Modern Cryptography, CRC.
5. A. Joux, Algorithmic Cryptanalysis, CRC.
6. J. Hoffstein, J. Pipher, and J. H. Silverman, An Introduction to Mathematical Cryptography, Springer.
7. S. Galbraith, Mathematics of Public Key Cryptography, CUP. ([version 2.0](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html))
8. Eindhoven University of Technology, Bachelor's course: [Introduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/)
9. Eindhoven University of Technology, Master's course: [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/)
10. USF Center for Cryptographic Research course: [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/)
11. Maryland Cybersecurity Center MOOC: [Cybersecurity Specialization](https://cyber.umd.edu/education/beyond-umd)
12. Stanford University MOOC: [A graduate course in applied cryptography](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/)

{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
