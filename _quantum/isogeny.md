---
title: "Isogeny based cryptography"
collection: quantum
permalink: /quantum/isogeny
excerpt:
date: 2021-12-01
venue: 
paperurl: 
citation: 
---
 
Isogeny-based cryptography is a kind of elliptic-curve cryptography, whose security relies on (various incarnations of) the problem of finding an explicit isogeny between two given isogenous supersingular elliptic curves over a finite field $\mathbb F_q$. However, given an elliptic curve $E$ in Weierstrass form over a finite field $\mathbb F_q$ and a point $P$ on $E$ of order $n$, one can compute a cyclic separable isogeny of degree $n$ using [Velu's formulas in SageMath](https://doc.sagemath.org/html/en/reference/arithmetic_curves/sage/schemes/elliptic_curves/ell_curve_isogeny.html) (implemented by [D. Shumow in 2009](https://arxiv.org/abs/0910.5370)).

Currently, quantum computers do not seem to make the isogeny-finding problem substantially easier. This contrasts with the standard discrete-logarithm based elliptic-curve cryptography which is not quantum-safe due to polynomial-time quantum algorithm by [P. W. Shor](https://arxiv.org/abs/quant-ph/9508027v2) from 1997. 


The [blog posts by Maria Santos (UCL)](https://mariascrs.github.io/posts.html) provide a nice introduction to isogeny-based cryptography.

Now let's look at some of the popular examples.

## Supersingular isogeny Diffie–Hellman (SIDH)

It was introduced by [L. De Feo, D. Jao, and J.  Plût](https://eprint.iacr.org/2011/506) in 2011 and uses the full ring of endomorphisms of supersingular elliptic curves, which is an order in a quaternion algebra, and the fact that [the supersingular isogeny graph is Ramanujan](https://gkorpal.github.io/files/pizer.pdf). This scheme is a reminiscent of the [Charles-Goren-Lauter (CGL) cryptographic hash function](https://eprint.iacr.org/2006/021) from 2006, which was [broken in 2020](https://arxiv.org/abs/2004.11495). Its current implementation is called [Supersingular Isogeny Key Encapsulation (SIKE)](https://sike.org/) and was submitted to the [NIST competition on post-quantum cryptography](https://csrc.nist.gov/projects/post-quantum-cryptography/post-quantum-cryptography-standardization) in 2017. An efficient algorithm for computing the endomorphism ring of a supersingular elliptic curve, under [certain assumptions](https://eprint.iacr.org/2018/371), would completely break the SIKE. The [SIDH also motivated](https://ellipticnews.wordpress.com/2020/12/24/sqisign/) the introduction of a new isogeny-based signature schemes like [Galbraith-Petit-Silva signature](https://eprint.iacr.org/2016/1154) and [Short Quaternion and Isogeny Signature (SQISign; pronounced "ski-sign")](https://eprint.iacr.org/2020/1240.pdf).

<!---- python
# Verifying the computations given on page 6 of the article by Craig Costello.
# Since the j-invariant of supersingular elliptic curves lies in F_{p^2}
# it is sufficient to work with quadratic extension of F_p.
# The prime p = 431 is chosen such that x^2+1 is irreducible since 431 = 3 (mod 4)
# hence F_{p^2} = F_{p}[x]/(x^2+1).
# Next we pick those supersingular elliptic curves which have (p+1)^2 = 432^2 
# F_{p^2}-rational points so that trace of frobenius is -2p and
# E(F_{p^2}) = E[p+1]. see Costello p. 8 and 11; Feo-Jao-Plut section 4.1.
sage: K.<a> = GF(431^2, name="a", modulus=x^2+1); K 
Finite Field in a of size 431^2
sage: E = EllipticCurve(K, [0,208*a+161,0,1,0]); E
Elliptic Curve defined by y^2 = x^3 + (208*a+161)*x^2 + x over 
Finite Field in a of size 431^2
sage: E.cardinality() # Schoof 1985
186624
sage: 186624 == 432^2
True
sage: E.abelian_group() # Rück 1987
Additive abelian group isomorphic to Z/432 + Z/432 embedded in Abelian group of
points on Elliptic Curve defined by y^2 = x^3 + (208*a+161)*x^2 + x over Finite
Field in a of size 431^2
sage: E.j_invariant()
364*a + 304
sage: P = E(350*a+68,0); P
(350*a + 68 : 0 : 1)
sage: P.order()
2
sage: phi = EllipticCurveIsogeny(E,P); phi  # Vélu 1971; not Montgomery form
Isogeny of degree 2 from Elliptic Curve defined by y^2 = x^3 + (208*a+161)*x^2 
+ x over Finite Field in a of size 431^2 to Elliptic Curve defined by y^2 = 
x^3 + (208*a+161)*x^2 + (343*a+209)*x + (363*a+398) over Finite Field in a 
of size 431^2
sage: phi.is_separable()
True
sage: phi.rational_maps()
((x^2 + (81*a - 68)*x + (190*a - 214))/(x + (81*a - 68)),
 (x^2*y + (162*a - 136)*x*y + y)/(x^2 + (162*a - 136)*x + (190*a - 213)))
sage: E2 = EllipticCurve(K, [0,208*a+161,0,343*a+209,363*a+398]); E2
Elliptic Curve defined by y^2 = x^3 + (208*a+161)*x^2 + (343*a+209)*x +
(363*a+398) over Finite Field in a of size 431^2
sage: P2 = phi(P); P2
(0 : 1 : 0)
sage: P2.order()
1
sage: E2.cardinality()
186624
sage: E2.abelian_group()
Additive abelian group isomorphic to Z/432 + Z/432 embedded in Abelian group of 
points on Elliptic Curve defined by y^2 = x^3 + (208*a+161)*x^2 + (343*a+209)*x + 
(363*a+398) over Finite Field in a of size 431^2
sage: E2.j_invariant()
344*a + 190
---->

**Update (Feb 02, 2022):** Using SageMath 9.5, one can implement SIDH in only 20 lines of code ([announcement](https://twitter.com/yx7__/status/1488775190733484035?s=20&t=v0cPtXdYUruLpWyR84k7SA)).

**Update (Jul 30, 2022):** SIKE broken by Wouter Castryck and Thomas Decru. The [SageMath implementation](https://research.nccgroup.com/2022/08/08/implementing-the-castryck-decru-sidh-key-recovery-attack-in-sagemath/) of this attack recovers the private key in few minutes. See the posts by [Steven Galbraith](https://ellipticnews.wordpress.com/2022/08/12/attacks-on-sidh-sike/) and [Lorenz Panny](https://yx7.cc/blah/2022-08-22.html) to understand the attack. One can find the current status of attacks [here](https://issikebrokenyet.github.io/). Here is a summary [posted by Luca De Feo](https://twitter.com/luca_defeo/status/1579249496890183680?s=20&t=_CfzxMrLWFMeEITRViw68Q):

![luca](https://pbs.twimg.com/media/FeqaAanWAAAGjGX?format=png)

**Update (Mar 26, 2023):** SQISign has new resources like [SQISign 2.0](https://eprint.iacr.org/2022/234), [SQISignHD](https://eprint.iacr.org/2023/436), and [Learning to SQI](https://learningtosqi.github.io/). 

**Update (Apr 25, 2023):** A [blogpost by Thomas Decru](https://www.esat.kuleuven.be/cosic/blog/an-efficient-key-recovery-attack-on-sidh/) explaing the SIDH attack.

**Upadate (Jan 21, 2024):** The [ALGANT Master's thesis](https://hdl.handle.net/20.500.12608/48936) by Riya Parankimamvila Mamachan about the mathematical aspects of the Castryck-Decru key recovery attack on SIDH.

### References

I have included the university location for the write-ups/videos by graduate students. The ones that I found the most useful are star marked (\*).
1. M. Pierrakea (ALGANT-Bordeaux 2016-17), [Supersingular isogeny key-exchange](https://www.math.u-bordeaux.fr/~ybilu/algant/documents/theses/Pierrakea.pdf)
2. \*D. Urbanik (Waterloo 2016-17), [A Friendly Introduction to Supersingular Isogeny Diffie-Hellman](https://www.math.toronto.edu/dburbani/work/friendlysidh.pdf) (Bonus: [video](https://www.youtube.com/watch?v=PW5Vsu57o9I) and [slides](https://www.math.toronto.edu/dburbani/work/sidh_talk_july_2016.pdf))
3. L. De Feo (2017), [Mathematics of Isogeny Based Cryptography](https://arxiv.org/abs/1711.04062) (Bonus: [slides](https://defeo.lu/docet/class/2017/05/26/isogenies-in-africa/))
4. S. Galbraith and F. Vercauteren (2017), [Computational problems in supersingular elliptic curve isogenies](https://eprint.iacr.org/2017/774)
5. L. Panny (TU Eindhoven 2017), [You could have invented Supersingular Isogeny Diffie-Hellman](https://yx7.cc/docs/sidh/ychi_sidh_slides.pdf)
6. M. Inés, A. Ali, and A. Best (Boston 2018), [Supersingular Isogeny Graphs and Quaternion Algebras](https://alexjbest.github.io/buntes/chapter-supersing-isog.html) (Bonus: [BUNTES Fall 2018](http://math.bu.edu/people/midff/buntes/fall2018.html))
7. S. Arpin (Boulder 2019) , [A Survey of Literature on Supersingular Isogeny Graphs](http://math.colorado.edu/~saar7867/SupersingularIsogenyLiterature.pdf)
8. \*C. Costello (2019), [Supersingular isogeny key exchange for beginners](https://eprint.iacr.org/2019/1321) (Bonus: [video](https://www.microsoft.com/en-us/research/video/post-quantum-cryptography-supersingular-isogenies-for-beginners/), [Companion SageMath notebook by Wojciech Nawrocki](https://voidma.in/posts/jupyter_notebooks/2020-07-03-sike.html), and [Computation verification by me using SageMath](https://gkorpal.github.io/files/Costello-Sage.pdf))
9. K. Lauter and J. Sotáková (2021), [Supersingular Isogeny Graphs in Cryptography](https://jana-sotakova.github.io/PCMI.html) (Bonus: [PCMI webpage](https://www.ias.edu/pcmi/2021-graduate-summer-school-course-descriptions) and [KLPT algorithm podcast](https://www.cryptography.fm/21))
10. P. Longa (2021), [Supersingular Isogeny-Based Cryptography: Implementation Aspects and Parameter Selection](https://irp.cdn-website.com/7fa75f95/files/uploaded/IBCSchool_Longa.pdf) (Bonus: [slides](https://www.patricklonga.com/talks) and [related video](https://www.youtube.com/watch?v=31NyfrHSAco))
11. J-J Chi-Domínguez (2021), [A quick journey on what SI[DH/KE] is](https://youtu.be/B_0osKMNN5k?t=462) (Bonus: [slides](https://jjchidguez.github.io/slides.html); the notation used for function composition is a bit confusing; here "Kummer line arithmetic" = Montgomery ladder + Vélu's formulas -- see the [original SIDH paper](https://eprint.iacr.org/2011/506).)


## Commutative supersingular isogeny Diffie–Hellman (CSIDH; pronounced "sea-side")
It was introduced by [W. Castryck, T. Lange, C. Martindale, L. Panny, and J. Renes](https://eprint.iacr.org/2018/383) in 2018 and uses the subring of $\mathbb F_p$-rational endomorphisms of supersingular elliptic curves, which is an order $O$ in an imaginary quadratic field. Moreover, the ideal-class group $\mathrm{cl}(O)$ is commutative, unlike the full ring of endomorphisms. This is an efficient variant of the [Couveignes-Rostovtsev–Stolbunov (CRS) scheme](https://eprint.iacr.org/2006/145) for which [the commutativity of ideal-class group](https://arxiv.org/abs/1012.4019) leads to a subexponential attack using the quantum algorithms by [G. Kuperberg](https://arxiv.org/abs/quant-ph/0302112) and [O. Regev](https://arxiv.org/abs/quant-ph/0406151) from 2004. The CSIDH also motivated the introduction of a new isogeny-based signature schemes like [SeaSign](https://eprint.iacr.org/2018/824) and [Commutative supersingular isogeny based Fiat-Shamir signatures (CSI-FiSH; pronounced "sea-fish")](https://eprint.iacr.org/2019/498).

### References

I have included the university location for the write-ups/videos by graduate students.
1. L. De Feo (2019), [Isogeny Graphs in Cryptography](https://defeo.lu/docet/talk/2019/07/29/wurzburg/) (Bonus: [David Jao on math.SE](https://math.stackexchange.com/users/268702/djao?tab=answers))
2. J. Sotáková (Amsterdam 2020), [Elliptic curves, isogenies, and endomorphism rings](https://jana-sotakova.github.io/writings/ANTS_school_exposition.pdf) (Bonus: [video](https://www.youtube.com/watch?v=hHD1tqFqjEQ))
3. Y.B. Ti (Auckland 2020), [Mathematics of Isogeny-based cryptography](https://www.youtube.com/watch?v=cefwCn7wy2Q)
4. T. Lange and L. Panny (2021), [(C)SIDH](https://www.hyperelliptic.org/tanja/teaching/isogeny-school21/) (Bonus: [L. Panny's notes](https://yx7.cc/docs/misc/isog_bristol_notes.pdf) and [Martindale-Panny article](https://www.martindale.info/car_article.pdf))
5. J.-F. Biasse (2021), [Ideal class group computations for isogeny-based cryptography](http://www.usf-crypto.org/class-groups/)
6. S. Galbraith (2023), [The Ideal Class Group Action on Supersingular Elliptic Curves](https://www.math.auckland.ac.nz/~sgal018/note-on-CSIDH-action.pdf)

## Recent developments

There are many new cryptosystems being developed, like [OSIDH](https://eprint.iacr.org/2020/985), [Séta](https://eprint.iacr.org/2019/1291) (broken), [SIAKE](https://eprint.iacr.org/2018/760), [SiGamal](https://eprint.iacr.org/2020/613), [B-SIDH](https://eprint.iacr.org/2019/1145) (broken), and [CTIDH](https://ctidh.isogeny.org/).

### References

1. The webpages for [SIKE](https://sike.org/) and [CSIDH](https://csidh.isogeny.org/index.html).
2. S. Galbraith's blog [ellipticnews](https://ellipticnews.wordpress.com/)
3. D. Jao's seminar at ANTS-XIV: [Isogeny-based cryptography: past, present, and future](https://www.youtube.com/watch?v=AoE-uQinzqU)
4. L. De Feo's presentations:
   * [Pirates of the CSIDH](https://defeo.lu/docet/youtube/2020/06/03/pkc/) (Bonus: [preprint](https://eprint.iacr.org/2019/1288))
   * [Are Isogenies for Real?](https://defeo.lu/docet/youtube/2021/01/12/rwc/) (Bonus: [discussion session](https://www.youtube.com/watch?v=EAe5dqWcxh4))
   * [What's next for isogeny based cryptography?](https://www.youtube.com/watch?v=IF7uRqViHPs) (Bonus: [slides](https://defeo.lu/docet/talk/2021/02/17/aimc/))
5. Isogeny-based Cryptography School: [https://isogenyschool2020.co.uk/schedule/](https://isogenyschool2020.co.uk/schedule/)
   * W. Castryck, [CSIDH on the surface (CSURF)](https://homes.esat.kuleuven.be/~wcastryc/summer_school_csurf.pdf), Week 3: Basic protocols (19-23rd July 2021)
   * L. De Feo, [Tools for designing protocols based on isogenies (VDF, ORPF,...)](https://defeo.lu/docet/assets/misc/2021-08-02-isogeny-school.pdf), Week 5: Advanced protocols (2-6th August 2021)
   * J. Sotáková, [Genus theory and attacking CSIDH-like cryptosystems](https://jana-sotakova.github.io/DDH/DDH.pdf), Week 6: Classical cryptanalysis (9-13th August 2021)
   * C. Costello, [Why Hyperelliptic? : Using Kummer arithmetic to optimize genus one isogeny computations](https://www.craigcostello.com.au/s/why-hyperelliptic.pdf), Week 9: Genus two (6-10th September 2021) 
   * D.J. Bernstein, [√élu: Faster computation of isogenies of large prime degree](https://velusqrt.isogeny.org/presentations.html), Week 10: Efficient computation of isogenies (13-17th September 2021)
6. [Cryptography FM](https://www.cryptography.fm) podcast (Nadim Kobeissi)
   * L. De Feo and H. Montgomery, [Cryptographic Group Actions and Applications](https://www.cryptography.fm/5), Episode 5 (27 Oct 2020)
   * B. Wesolowski, [The supersingular isogeny path and endomorphism ring problems are equivalent](https://www.cryptography.fm/21)), Episode 21 (24 Aug 2021)
7. [Security, Cryptography, Whatever](https://securitycryptographywhatever.buzzsprout.com/) podcast (Deirdre Connolly, Thomas Ptacek, and David Adrian)
   * G. Tankersley, [PAKEs, oPRFs, algebra,...](https://securitycryptographywhatever.buzzsprout.com/1822302/9439685-pakes-oprfs-algebra-feat-george-tankersley), Episode 8 (26 Oct 2021)
   * [Hertzbleed](https://securitycryptographywhatever.buzzsprout.com/1822302/10812724-hertzbleed), Episode 18 (17 Jun 2022)
   * S. Galbraith, [Hot Cryptanalytic Summer](https://securitycryptographywhatever.buzzsprout.com/1822302/11123170-hot-cryptanalytic-summer-feat-steven-galbraith), Season 2, Episode 2 (11 Aug 2022)
8. Workshop on Elliptic Curve Cryptography (ECC): [https://eccworkshop.org/](https://eccworkshop.org/)
9. Algorithmic Number Theory Symposium (ANTS): [https://antsmath.org](https://antsmath.org)
10. Simons Collaboration on Arithmetic Geometry, Number Theory, and Computation: [https://simonscollab.icerm.brown.edu/](https://simonscollab.icerm.brown.edu/)
11. Virtual math seminar on open conjectures in number theory and arithmetic geometry (VaNTAGe): [https://sites.google.com/view/vantageseminar](https://sites.google.com/view/vantageseminar)
12. ISOCRYPT - Isogeny-based Toolbox for Post-quantum Cryptography: [https://www.esat.kuleuven.be/cosic/projects/isocrypt/](https://www.esat.kuleuven.be/cosic/projects/isocrypt/)
13. The Isogeny Club: [https://the-isogeny-club.github.io/](https://the-isogeny-club.github.io/)

<!----- 
2. Joost Renes, Improved Classical Cryptanalysis of SIKE in Practice, [IACR Practice and Theory of Public-Key Cryptography 2020](https://pkc.iacr.org/2020/), paper presentation (Jun 04, 2020). ([video](https://www.youtube.com/watch?v=QGIEbIzt6gk) and [paper](https://pkc.iacr.org/2020/program.php))
4. Antonin Leroux, Faster Computation of isogenies of large prime degree, [Fourteenth Algorithmic Number Theory Symposium, ANTS-XIV](https://www.math.auckland.ac.nz/~sgal018/ANTS/schedule.html), Paper presentation (July 02, 2020). ([video](https://www.youtube.com/watch?v=BA-mknsDMaY) and [paper](https://velusqrt.isogeny.org/))
5. Thomas Decru + Daniele Cozzo + Craig Costello, CSIDH on the surface + Sashimi + supersingular isogeny problem, [PQCrypto 2020](https://pqcrypto2020.inria.fr/program/), Isogeny-based and Number Theoretic-based Cryptography. ([videos](https://www.youtube.com/playlist?list=PLv9DOvVF-X96M-O2obeLYzhZ0Qj15p_wb) and [papers](https://pqcrypto2020.inria.fr/program/))
7. Chloe Martindale, Bruhat-Tits trees as a tool for isogeny-based cryptography, [Front Range Number Theory Day](https://sites.google.com/colorado.edu/front-range-number-theory-day/spring-2021) (April 24, 2021). ([video](https://www.youtube.com/watch?v=5f3SGbrQlkk) 360p)
1. Christophe Petit. Post-quantum cryptography from supersingular isogeny problems?, [Microsoft Research Seminar](https://www.microsoft.com/en-us/research/video/post-quantum-cryptography-supersingular-isogeny-problems/) (Aug 03, 2017). ([video](https://www.youtube.com/watch?v=eHkmO7bFaSc))
8. Lukas Zobernig. Lectures on Complex Multiplication, [University of Auckland Number Theory Reading Group 2020](https://uoantrg.wordpress.com/) (May - June, 2020). ([videos](https://youtube.com/playlist?list=PLDSicQbDroeqlQ8cce4JtExbL4aZ67bgk), [lec1notes](https://uoantrg.files.wordpress.com/2020/05/ell_over_c_1.pdf), [lec2notes](https://uoantrg.files.wordpress.com/2020/05/ell_over_c_2.pdf), and [lec3notes](https://uoantrg.files.wordpress.com/2020/07/ell_cm_1-1.pdf))
10. Tanja Lange and Lorenz Panny. Isogeny-based cryptography (Introduction to SIDH and CSIDH), [Isogeny-based Cryptography School](https://isogenyschool2020.co.uk/), Week 3 (July 19-23, 2021): Basic protocols. ([videos](https://www.youtube.com/playlist?list=PL6hzlGxGIS1Cnx3XS7ZD4wjcTmHqOEpTS), [slides+notes+exercises by Tanja](https://www.hyperelliptic.org/tanja/teaching/isogeny-school21/), [notes by Lorenz](https://yx7.cc/docs/misc/isog_bristol_notes.pdf), and [extra resources](https://hyperelliptic.org/tanja/teaching/pqcrypto21/)).
8. Sarah Arpin, [Good Primes for Supersingular 2, 3-Isogeny Graphs](http://math.colorado.edu/~saar7867/GoodPrimes.pdf)
7. Chloe Martindale, [Isogeny graphs of abelian varieties and applications to the Discrete Logarithm Problem](https://www.martindale.info/Rennes.pdf)
9. Lukas Zobernig, [Genus 2 Curves in Small Characteristic](https://www.math.auckland.ac.nz/~lzob857/papers/g2curves.pdf)
2. The cr.yp.to blog (Daniel J. Bernstein): [https://blog.cr.yp.to/](https://blog.cr.yp.to/)
3. Chole Martindale's talks: [https://www.martindale.info/talks/](https://www.martindale.info/talks/)
4. Luca De Feo's talks: [https://defeo.lu/docet/](https://defeo.lu/docet/)
5. Lorenz Panny's docs: [https://yx7.cc/docs/](https://yx7.cc/docs/)
6. Cloudflare Blog ([Cloudflare Research](https://research.cloudflare.com/)): [https://blog.cloudflare.com/tag/security/](https://blog.cloudflare.com/tag/security/) ([Google-Cloudflare Experiment](https://blog.cloudflare.com/the-tls-post-quantum-experiment/); [Sizing Up Post-Quantum Signatures](https://blog.cloudflare.com/sizing-up-post-quantum-signatures/))
1. Boston University Number Theory Expository Seminar: [http://math.bu.edu/people/angusmca/buntes/index.html](http://math.bu.edu/people/angusmca/buntes/index.html)
2. University of Auckland Number Theory Reading Group (Tristan Pang): [https://uoantrg.wordpress.com/](https://uoantrg.wordpress.com/)
5. Research Directions in Number Theory: Women in Numbers IV, Springer ([arXiv:1806.05709](https://arxiv.org/abs/1806.05709) and [arXiv:1804.04063
](https://arxiv.org/abs/1804.04063))
6. Proceedings of the Fourteenth Algorithmic Number Theory Symposium, The Open Book Series ([arXiv:1910.03180](https://arxiv.org/abs/1910.03180), [arXiv:2003.10118](https://arxiv.org/abs/2003.10118), [arXiv:2004.11495](https://arxiv.org/abs/2004.11495), and [arXiv:2003.00633](https://arxiv.org/abs/2003.00633) -- [paper presentation lectures](https://www.youtube.com/channel/UCdSSlKPQ57S8AlHaiclp26Q/videos))
6. D.A. Cox, Primes of the form $$x^2+ny^2$$: Fermat, Class Field Theory, and Complex Multiplication, Wiley.
2. Joseph Silverman, Arithmetic of Elliptic Curves, Springer.
3. John Voight, Quaternion Algebras, Springer ([latest version](https://math.dartmouth.edu/~jvoight/quat.html))
4. Giuliana Davidoff, Peter Sarnak, and Alain Valette, Elementary number theory, group theory, and Ramanujan graph, Cambridge University Press
----->
