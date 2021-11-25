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
1. 25th IAS Program for Women and Mathematics - [Mathematics of Modern Cryptography](https://www.ias.edu/math/wam/2018)
2. MasterMath (Dutch Master’s Degree Programme in Mathematics) - [Post-quantum cryptography](https://hyperelliptic.org/tanja/teaching/pqcrypto21/)
3. USF Center for Cryptographic Research - [Quantum Algorithms and Complexity](https://www.usf-crypto.org/mat-4930/)
4. Simons Institue - [Workshop on Quantum Cryptanalysis of Post-Quantum Cryptography](https://simons.berkeley.edu/workshops/lattices2020-quantum2020-joint) 
5. Latincrypt 2021 - [ASCRYPTO cryptography summer school](https://www.urosario.edu.co/ascrypto/home/)
6. Post-quantum cryptography (PQCrypto): [https://pqcrypto.org/](https://pqcrypto.org/)

{% include base_path %}


{% for post in site.quantum %}
  {% include archive-single.html %}
{% endfor %}
