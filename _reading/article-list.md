---
title: "Good Articles"
collection: reading
permalink: /reading/article-list
excerpt:
date: 2023-05-13
venue: 
paperurl: 
citation: 
---

Following are some of the mathematics articles that I would recommend reading. The inspiration for this list came from the anthologies like [Who Gave You the Epsilon? And Other Tales of Mathematical History](https://www.maa.org/press/maa-reviews/who-gave-you-the-epsilon-and-other-tales-of-mathematical-history) and [Biscuits of Number Theory](https://www.maa.org/press/maa-reviews/biscuits-of-number-theory).

Here I have divided articles between applied mathematics ([computational mathematics](https://nces.ed.gov/ipeds/cipcode/cipdetail.aspx?y=56&cip=27.0303)) and pure mathematics ([algebra and number theory](https://nces.ed.gov/ipeds/cipcode/cipdetail.aspx?y=56&cip=27.0102)). Loosely speaking, computer science is a specialization within the discipline of computational mathematics (not to be confused with [computational science](https://nces.ed.gov/ipeds/cipcode/cipdetail.aspx?y=56&cip=30.3001)), and computer engineering is a specialization within the discipline of electrical engineering (closely related to physics and applied mathematics), for details see [this 1989 report by the ACM Education Board](https://doi.org/10.1145/63238.63239). Moreover, I believe in the exsitence of the following hierarchy in [STEM fields](https://fas.org/sgp/crs/misc/R42642.pdf), i.e. outer one assumes results from the inner ones, illustrated alongside using elliptic curve cryptography:

<p>
<center>
    <a href="https://gkorpal.github.io/reading/article-list">
      <img alt="STEM" src="https://gkorpal.github.io/images/stem.jpg" width="300" height="300" class="center">
  </a>
  <a href="https://gkorpal.github.io/reading/article-list">
     <img alt="crypt" src="https://gkorpal.github.io/images/crypt.jpg" width="300" height="300" class="center">
  </a>
   </center>
 </p>


Note that the order of authors' names in pure mathematics and applied mathematics (similar to science and engineering) articles tend to have a different meaning, for details see [this 1992 paper by Andrew Appel](https://doi.org/10.1145/131080.131091) and [this 2004 statement by the AMS](http://www.ams.org/profession/leaders/CultureStatement04.pdf). 

One might need university library membership to access some of these articles (or use the power of internet). I have arranged the articles in reverse chronological order (from the latest to the oldest). 

* [Applied Mathematics](#applied-mathematics) 
  * [Expository](#expository)
  * [Research](#research)
* [Pure Mathematics](#pure-mathematics)
  * [Expository](#expository-1)
  * [Research](#research-1)


# Applied Mathematics
<img src="/images/crash.png" alt="">

## Expository

* A. Menezes and D. Stebila, Challenges in Cryptography, _IEEE Security & Privacy_ **19** (2021), no. 2, 70--73. doi:[10.1109/MSEC.2021.3049730](https://doi.org/10.1109/MSEC.2021.3049730)
* P. C. van Oorschot, Toward Unseating the Unsafe C Programming Language,  _IEEE Security & Privacy_ **19** (2021), no. 2, 4--6. doi:[10.1109/MSEC.2020.3048766](https://doi.org/10.1109/MSEC.2020.3048766)
* T. Lindell, Secure multiparty computation, _Communications of the ACM_ **64** (2021), no. 1, 86--96. doi:[10.1145/3387108](https://doi.org/10.1145/3387108), [Stable URL](https://cacm.acm.org/magazines/2021/1/249459-secure-multiparty-computation/fulltext)
* C. Peng, J. Chen, S. Zeadally and D. He, Isogeny-Based Cryptography: A Promising Post-Quantum Technique, _IEEE IT Professional_ **21** (2019), no. 6, 27--32. doi:[10.1109/MITP.2019.2943136](https://doi.org/10.1109/MITP.2019.2943136) \[Contains nice illustrations.\]
* C. Martindale and L. Panny, Isogeny-based cryptography, _Computeralgebra-Rundbrief_ (Computer Algebra Newsletter) **65** (2019), no. 1, 12--17. [Stable URL](https://fachgruppe-computeralgebra.de/data/CA-Rundbrief/car65.pdf), [preprint](https://www.martindale.info/car_article.pdf) \[Contains nice illustrations.\]
* J. Waldo, A Hitchhiker’s Guide to the Blockchain Universe: Blockchain remains a mystery, despite its growing acceptance, _ACM Queue_ **16** (2018), no. 6, 15 pp. doi:[10.1145/3305263.3305265](https://doi.org/10.1145/3305263.3305265), [Stable URL](https://queue.acm.org/detail.cfm?id=3305265)
* A. Narayanan and J. Clark, Bitcoin’s Academic Pedigree: The concept of cryptocurrencies is built from forgotten ideas in research literature, _ACM Queue_ **15** (2017), no. 4, 30 pp. doi:[10.1145/3134434.3136559](https://doi.org/10.1145/3134434.3136559), [Stable URL](https://queue.acm.org/detail.cfm?id=3136559) \[An equivalent quality video exposition by Grant Sanderson (3Blue1Brown) on [YouTube](https://www.youtube.com/watch?v=bBC-nXj3Ng4)\]
* K. Lauter, Postquantum Opportunities: Lattices, Homomorphic Encryption, and Supersingular Isogeny Graphs, _IEEE Security & Privacy_ **15** (2017), no. 4, 22--27. doi:[10.1109/MSP.2017.3151338](https://doi.org/10.1109/MSP.2017.3151338) 
* H. Cohn, A conceptual breakthrough in sphere packing, _Notices Amer. Math. Soc._ **64** (2017), no. 2,  102--115. doi:[10.1090/noti1474](https://doi.org/10.1090/noti1474)
* N. Koblitz and A. Menezes, A Riddle Wrapped in an Enigma, _IEEE Security & Privacy_ **14** (2016), no. 6, 34--42. doi:[10.1109/MSP.2016.120](https://doi.org/10.1109/MSP.2016.120) \[There are equivalent quality video expositions by [Numberphile](https://www.youtube.com/watch?v=ulg_AHBOIQU) (2013) and [Computerphile](https://www.youtube.com/watch?v=nybVFJVXbww) (2018)\]
* N. Koblitz and A. Menezes, Cryptocash, cryptocurrencies, and cryptocontracts, _Designs, Codes and Cryptography_ **78** (2016), no. 1, 87--102. doi:[10.1007/s10623-015-0148-5](https://doi.org/10.1007/s10623-015-0148-5) 
* J. Bonneau, A. Miller, J. Clark, A. Narayanan, J. A. Kroll and E. W. Felten, SoK: Research Perspectives and Challenges for Bitcoin and Cryptocurrencies, _Proc. of S&P (Oakland) 2015_. doi: [10.1109/SP.2015.14](https://doi.org/10.1109/SP.2015.14).
* S. Kamara, Encrypted Search, _XRDS: Crossroads, The ACM Magazine for Students_ **21** (2015), no. 3, 30--34. doi:[10.1145/2730908](https://doi.org/10.1145/2730908), [Stable URL](https://xrds.acm.org/article.cfm?aid=2730908)
* D. Boneh, A. Sahai and B. Waters, Functional encryption: a new vision for public-key cryptography, _Communications of the ACM_ **55** (2012), no. 11, 56--64. doi:[10.1145/2366316.2366333](https://doi.org/10.1145/2366316.2366333), [Stable URL](https://cacm.acm.org/magazines/2012/11/156588-functional-encryption/fulltext)
* C. P. Pfleeger, Crypto: Not Just for the Defensive Team, _IEEE Security & Privacy_ **8** (2010), no. 2, 63--66. doi:[10.1109/MSP.2010.65](https://doi.org/10.1109/MSP.2010.65)
* C. Christensen, Polish Mathematicians Finding Patterns in Enigma Messages, _Math. Mag._ **80** (2007), no. 4, 247--273.  [Stable URL](https://www.jstor.org/stable/27643040) 
* R. Gennaro, Randomness in cryptography, _IEEE Security & Privacy_ **4** (2006), no. 2, 64--67. doi:[10.1109/MSP.2006.49](https://doi.org/10.1109/MSP.2006.49)
* K. Lauter, The advantages of elliptic curve cryptography for wireless security, _IEEE Wireless Communications_ **11** (2004), no. 1, 62--67. doi:[10.1109/MWC.2004.1269719](https://doi.org/10.1109/MWC.2004.1269719)
* B. Schneier, Cryptography: the importance of not being different, _IEEE Computer_ **32** (1999), no. 3, 108--109. doi:[10.1109/2.751335](https://doi.org/10.1109/2.751335)
* N. Koblitz, Cryptography as a teaching tool, _Cryptologia_ **21** (1997), no. 4, 317--326. doi:[10.1080/0161-119791885959](https://doi.org/10.1080/0161-119791885959)

## Research

* R. Wang, Y. Shoshitaishvili, C. Kruegel, and G. Vigna, Steal This Movie: Automatically Bypassing DRM Protection in Streaming Media Services, _USENIX 13_. [Stable link](https://www.usenix.org/conference/usenixsecurity13/technical-sessions/paper/wang_ruoyu) 
* D. Boneh and M. Franklin, Identity-Based Encryption from the Weil Pairing, _Proc. of Crypto 2001_.  doi:[10.1007/3-540-44647-8_13](https://doi.org/10.1007/3-540-44647-8_13) \[The full version of this paper was published in SICOMP **32** (2003), no. 3. doi:[10.1137/S0097539701398521](https://doi.org/10.1137/S0097539701398521) \]
* M. Fellows and N. Koblitz, Kid Krypto, _Proc. of Crypto 1992_. doi:[10.1007/3-540-48071-4_27](https://doi.org/10.1007/3-540-48071-4_27)
* D. Chaum and E. van Heyst, Group Signatures, _Proc. of Eurocrypt 1991_. doi:[10.1007/3-540-46416-6_22](https://doi.org/10.1007/3-540-46416-6_22)
* N. Koblitz, Elliptic curve cryptosystems. _Math. Comp._ **48** (1987), no. 177, 203--209. doi:[10.2307/2007884](https://doi.org/10.2307/2007884)
* V. S. Miller, Use of Elliptic Curves in Cryptography, _Proc. of Crypto 1985_. doi:[10.1007/3-540-39799-X_31](https://doi.org/10.1007/3-540-39799-X_31)
* A. Shamir, Identity-Based Cryptosystems and Signature Schemes, _Proc. of IACR Crypto 1984_. doi:[10.1007/3-540-39568-7_5](https://doi.org/10.1007/3-540-39568-7_5)
* A. C. Yao, Protocols for secure computations, _Proc. of IEEE Symp. on FOCS 1982_. doi:[10.1109/SFCS.1982.38](httpsL//doi.org/10.1109/SFCS.1982.38) 
* M. Rejewski, An Application of the Theory of Permutations in Breaking the Enigma Cipher, _Zastos. Mat. \[Appl. Math. (Warsaw)\]_, **16** (1980), no. 4, 543--559. doi:[10.4064/am-16-4-543-559](https://doi.org/10.4064/am-16-4-543-559)
 
As one can see, my knowledge of computer science is limited to cryptography. Note that the key theoretical cryptography results are generally announced in the conferences like [Crypto](https://www.iacr.org/meetings/crypto/), [Eurocrypt](https://www.iacr.org/meetings/eurocrypt/), [Asiacrypt](https://www.iacr.org/meetings/asiacrypt/), [TCC](https://www.iacr.org/meetings/tcc/), [FOCS](http://ieee-focs.org/), [STOC](http://acm-stoc.org/), [ANTS](https://antsmath.org/), and [AGC2T](https://www.ams.org/books/conm/770/). On the other hand, the key applied cryptography results are generally announced in the conferences like [S&P (Oakland)](https://www.ieee-security.org/TC/SP-Index.html), [CCS](https://www.sigsac.org/ccs.html), [CHES](https://www.iacr.org/meetings/ches/), and [USENIX Security](https://www.usenix.org/conferences/byname/108). A more comprehensive list of relevant conferences can be found [here](https://sec-deadlines.github.io/).

# Pure Mathematics

<img src="/images/pure.png" alt="">

## Expository

* J. S. Chahal, What Do Networks and Elliptic Curves Have in Common?, _Amer. Math. Monthly_ **130** (2023), no. 2, 158-175, doi:[10.1080/00029890.2022.2141548](https://doi.org/10.1080/00029890.2022.2141548)
* W. D’Alessandro, Proving quadratic reciprocity: explanation, disagreement, transparency and depth, _Synthese_ **198** (2021), 8621--8664. doi:[10.1007/s11229-020-02591-6](https://doi.org/10.1007/s11229-020-02591-6)
* F. Oort, The Weil Conjectures, _Nieuw Arch. Wiskd. (5)_ **15** (2014), no. 6, 211--219. [Stable URL](http://www.nieuwarchief.nl/serie5/pdf/naw5-2014-15-3-211.pdf)  (There is a calculation error in the last line of the middle column of p. 214, $\alpha^{10},\beta^{10} = \mp 32i$).
* C. S. Dalawat, Classical Reciprocity Laws, _Asia Pac. Math. Newsl._ **4** (2014), no. 4,  5--9. [Stable URL](http://www.asiapacific-mathnews.com/04/0404/0005_0009.pdf)
* F. Oort, Prime Numbers, _ICCM Not._ **1** (2013), no. 2, 60–78. doi:[10.4310/ICCM.2013.v1.n2.a8](https://dx.doi.org/10.4310/ICCM.2013.v1.n2.a8) 
* U. A. Rozikov, What   are   p-adic   Numbers? What   are   they   used   for?, _Asia Pac. Math. Newsl._ **3** (2013),   no. 4, 1–6. [Stable URL](http://www.asiapacific-mathnews.com/03/0304/0001_0006.pdf)
* R. Sreekantan, Yitang Zhang and The Twin Primes Conjecture, _At Right Angles_ **2** (2013), no. 3, 14--17. [Stable URL](https://publications.azimpremjiuniversity.edu.in/1682/)
* A. Rice and E. Brown, Why Ellipses Are Not Elliptic Curves, _Math. Mag._ **85** (2012), no. 3, 163--176. doi:[10.4169/math.mag.85.3.163](https://doi.org/10.4169/math.mag.85.3.163), [Stable URL](https://www.jstor.org/stable/10.4169/math.mag.85.3.163)
* G. Frey, The Arithmetic Behind Cryptography, _Notices Amer. Math. Soc._ **57** (2010), no. 3, 366-374. [Stable URL](http://www.ams.org/notices/201003/rtx100300366p.pdf)
* A. Granville and G. Martin, Prime Number Races, _Amer. Math. Monthly_ **113** (2006), no. 1, 1--33. [Stable URL](https://www.jstor.org/stable/27641834)
* D. Khurana, On GCD and LCM in Domains – A Conjecture of Gauss, _Resonance_ **8** (2003), no. 6, 72--79. [Stable URL](https://www.ias.ac.in/article/fulltext/reso/008/06/0072-0079)
* J. B. Conrey, The Riemann Hypothesis, _Notices Amer. Math. Soc._ **50** (2003), no. 3, 341--353. [Stable URL](http://www.ams.org/notices/200303/fea-conrey-web.pdf)
* S. Ahlgren and K. Ono, Adding and counting: The arithmetic of partitions, _Notices Amer. Math. Soc._ **48** (2001), no. 9, 978--984. [Stable URL](http://www.ams.org/notices/200109/fea-ahlgren.pdf)
* P. Stevenhagen and H. W. Lenstra, Chebotarëv and his Density Theorem, _Math. Intelligencer_ **18** (1996), no. 2, 26--37. doi:[10.1007/BF03027290](https://doi.org/10.1007/BF03027290)
* N. Schappacher and R. Schoof,  Beppo Levi and the arithmetic of elliptic curves, _Math. Intelligencer_ **18** (1996), no. 1, 57--69. doi:[10.1007/BF03024818](https://doi.org/10.1007/BF03024818)
* J. Shallit, Origins of the analysis of the Euclidean algorithm, _Historia Mathematica_ **21** (1994), no. 4, 401--419. doi:[10.1006/hmat.1994.1031](https://doi.org/10.1006/hmat.1994.1031)
* E. Bombieri, Prime Territory, _The Sciences_ **32** (1992), no. 5, 30--36. doi:[10.1002/j.2326-1951.1992.tb02416.x](https://doi.org/10.1002/j.2326-1951.1992.tb02416.x)
* H. M. Edwards, Fermat's Last Theorem, _Scientific American_ **239** (1978), no. 4, 104–-122. doi: [10.1038/scientificamerican1078-104](https://doi.org/10.1038/scientificamerican1078-104), [Stable URL](https://www.jstor.org/stable/24955826)
* D. Zagier, The first 50 million prime numbers, _Math. Intelligencer_ **1** (1977), no. 1, 7--19. doi:[10.1007/BF03039306](https://doi.org/10.1007/BF03039306)
* B. L. van der Waerden, Hamilton's Discovery of Quaternions, _Math. Mag._ **49** (1976), no. 5, 227--234. doi:[10.2307/2689449](https://doi.org/10.2307/2689449), [Stable URL](https://www.jstor.org/stable/2689449)
* M. Davis and R. Hersh, Hilbert's 10th Problem,  _Scientific American_ **229** (1973), no. 5, 84--91. doi: [10.1038/scientificamerican1173-84](https://doi.org/10.1038/scientificamerican1173-84), [Stable URL](https://www.jstor.org/stable/24923245)

I have fond memories of reading expository articles in Indian magazines like Junior Mathematician (published by AMTI, Chennai) and Bona Mathematica (published by BP, Pune), which were similar to the Soviet era periodicals like Kvant (published by Nauka) and Little Mathematics Library (english translations published by Mir). Unfortunately, they are not available online (but were accessible without university library membership). However, [At Right Angles](https://azimpremjiuniversity.edu.in/at-right-angles) (published by APU, Bengaluru) and [Resonance](https://www.ias.ac.in/Journals/Resonance_%E2%80%93_Journal_of_Science_Education) (published by  IAS, Bengaluru) are  the current alternatives to these which are available online. 

The Mathematical Association of America (MAA) publishes many exposition focused journals like the American Mathematical Monthly, Mathematics Magazine, the College Mathematics Journal and Math Horizons, but I haven't been able to access latest issues via my University library (archives are available via JSTOR). Moreover, the [Princeton Companion to Mathematics](https://press.princeton.edu/books/hardcover/9780691118802/the-princeton-companion-to-mathematics) contains many original expository articles about almost every topic in maths.

## Research

* A. Granville,  Squares in Arithmetic Progressions and Infinitely Many Primes, _Amer. Math. Monthly_ **124** (2017), no. 10, 951--954. doi:[10.4169/amer.math.monthly.124.10.951](https://doi.org/10.4169/amer.math.monthly.124.10.951), [Stable URL](https://www.jstor.org/stable/10.4169/amer.math.monthly.124.10.951)
* H. M. Stark, A complete determination of the complex quadratic fields of class-number one, _Michigan Math. J._ **14** (1967), no. 1, 1--27, doi:[10.1307/mmj/1028999653](http://projecteuclid.org/euclid.mmj/1028999653)
* K. F. Roth, Rational approximations to algebraic numbers, _Mathematika_ **2** (1955), no. 1, 1--20. doi:[10.1112/S0025579300000644](https://doi.org/10.1112/S0025579300000644)
* I. Niven, A simple proof that $\pi$ is irrational, _Bull. Amer. Math. Soc._ **53** (1947), no. 6, 509--509. [Stable URL](https://projecteuclid.org/journals/bulletin-of-the-american-mathematical-society-new-series/volume-53/issue-6/A-simple-proof-that-pi-is-irrational/bams/1183510788.full) (this method was later [generalized by A. E. Parks](https://www.jstor.org/stable/2322291))
