---
layout: archive
title: "Computer safe cryptography"
permalink: /computer/
author_profile: true
redirect_from:
  - /jotting/computer
  
---

Here we discuss the cryptosystems which play an important role in internet security. These are considered secure against computers built using classical physics theories (binary, electronic, digital, programmable,...).

To get started, I would recommend the following:

|S. No.| Resource |
|------|----------|
|1 | [Lectures on Cryptography](https://shrek.unideb.hu/~tengely/crypto/webwork-mini.html) - Szabolcs Tengely (Debrecen, 2020)|
|2 | [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf) - David Kohel (SageMath, July 2008)|
|3 | Introduction to Cryptography with Open-Source Software - Alasdair McAndrew (CRC Press, 2011)|
|4 | Introduction to Modern Cryptography -  Jonathan Katz and Yehuda Lindell (CRC Press, 2007) |
|5 | An Introduction to Mathematical Cryptography - Jeffrey Hoffstein et al. (Springer, 2008) |
|6 | [Mathematics of Public Key Cryptography](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html) - Steven D. Galbraith (CUP, Oct 2018)|
|7 | [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/) - Jean-Francois Biasse (USF, 2018-2020) |
|8 | [Introduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/) - Tanja Lange (TU/e, 2021) |
|9 | [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/) - Tanja Lange (TU/e, 2021) |
|10| [Coursera MOOC: Cryptography I and II](https://www.coursera.org/instructor/~774) - Dan Boneh (Stanford) |
|11| [Coursera MOOC: Cryptography](https://www.coursera.org/instructor/~79127) - Jonathan Katz (Maryland) |

<!---- Matasano, [Cryptopals Challenges](https://cryptopals.com/) ---->

{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
