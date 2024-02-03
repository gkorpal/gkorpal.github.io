---
layout: archive
title: "Classical computer safe cryptography"
permalink: /computer/
author_profile: true
redirect_from:
  - /jotting/computer
  
---

Here we discuss the cryptosystems which play an important role in internet security. These are considered secure against computers built using classical physics theories (binary, electronic, digital, programmable,...).

To get started, one can consider the following resources:

|S. No.| Books/lecture notes/video lectures |
|------|----------|
|1 | [Lectures on Cryptography](https://shrek.unideb.hu/~tengely/crypto/webwork-mini.html) - Szabolcs Tengely (Debrecen, 2020)|
|2 | [Chalk Talk Cryptography](https://www.youtube.com/playlist?list=PLMItfTVgwEAvTX4-sZkcF5s3-l1JDocY0) - Kelsey Houston-Edwards (YouTube, 2022) |
|3 | [Introduction to Cryptography and Coding Theory](https://www.usf-crypto.org/mad-4471/) - Jean-Francois Biasse (USF, 2018-2020) |
|4 | [Introduction to Cryptology](https://www.hyperelliptic.org/tanja/teaching/CS21/) - Tanja Lange (TU/e, 2021) |
|5 | [Cryptology](https://www.hyperelliptic.org/tanja/teaching/crypto21/) - Tanja Lange (TU/e, 2021) |
|6| [Coursera MOOC: Cryptography I and II](https://www.coursera.org/instructor/~774) - Dan Boneh (Stanford) |
|7| [Coursera MOOC: Cryptography](https://www.coursera.org/instructor/~79127) - Jonathan Katz (Maryland) |
|8 | [Introduction to Modern Cryptography](http://www.cs.umd.edu/~jkatz/imc.html) -  Jonathan Katz and Yehuda Lindell (CRC Press, 2021) |
|9 | [An Introduction to Mathematical Cryptography](https://www.math.brown.edu/johsilve/MathCryptoHome.html) - Jeffrey Hoffstein et al. (Springer, 2014) |
|10 | [Mathematics of Public Key Cryptography](https://www.math.auckland.ac.nz/~sgal018/crypto-book/crypto-book.html) - Steven D. Galbraith (CUP, Oct 2018)|


<!---- Matasano, [Cryptopals Challenges](https://cryptopals.com/) ---->

{% include base_path %}


{% for post in site.computer %}
  {% include archive-single.html %}
{% endfor %}
