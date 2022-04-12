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
4. R. Ostrovsky, [Foundations of Cryptography](http://web.cs.ucla.edu/~rafail/PUBLIC/OstrovskyDraftLecNotes2010.pdf), Winter 2010.
5. Cryptopals, [the cryptopals crypto challenges](https://cryptopals.com/)
6. J. Katz and Y. Lindell, Introduction to Modern Cryptography, CRC + [Maryland Cybersecurity Center MOOC](https://cyber.umd.edu/education/beyond-umd)
7. D. Boneh and V. Shoup, [A graduate course in applied cryptography](http://toc.cryptobook.us/) + [Stanford University MOOC](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/)
8. A. Joux, Algorithmic Cryptanalysis, CRC.
9. J. Hoffstein, J. Pipher, and J. H. Silverman, An Introduction to Mathematical Cryptography, Springer.
10. S. Galbraith, Mathematics of Public Key Cryptography, CUP. ([version 2.0](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html))
11. USF Center for Cryptographic Research course: [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/)
12. Eindhoven University of Technology, Bachelor's course: [Introduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/)
13. Eindhoven University of Technology, Master's course: [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/)


{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
