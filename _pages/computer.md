---
layout: archive
title: "Computer safe cryptography"
permalink: /computer/
author_profile: true
redirect_from:
  - /jotting/computer
  
---

### General online courses
1. Eindhoven University of Technology, Bachelor's course: [Intorduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/)
2. Eindhoven University of Technology, Master's course: [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/)
3. USF Center for Cryptographic Research: [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/)
4. Maryland Cybersecurity Center: [Cybersecurity Specialization](https://cyber.umd.edu/education/beyond-umd)
5. Stanford University: [A graduate course in applied cryptography](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/)

{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
