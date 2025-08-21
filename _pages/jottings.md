---
layout: archive
title: "Jottings"
permalink: /jottings/
author_profile: true
---

> Mathematical reasoning may be regarded rather schematically as the exercise of a combination of two facilities, which we may call intuition and ingenuity. 
> -[Alan M. Turing](https://en.wikiquote.org/wiki/Alan_Turing)

Here are some resources related to cryptography and mathematics that I found useful.

| [Cryptography](#cryptography) | [Math tech](#math-tech) |
| ----------------------------- | ----------------------- |
| [Computationally secure cryptography](#computationally-secure-cryptography) | [Git](#git) |
| [Unconditionally secure cryptography](#unconditionally-secure-cryptography) | [Markdown](#markdown) |
|                                                                             | [TeX](#tex) |
|                                                                             | [Julia](#julia) |


# Cryptography

<p>
<center>
<a href="https://gkorpal.github.io/files/Crypto_goals.tex">
     <img alt="mindmap" src="https://gkorpal.github.io/images/Crypto_goals.png" class="center"
          width="400" height="400">
</a>
</center>
</p>

To get started, one can consider the following resources:

|  Blog posts/interviews | Lecture notes/books (free and great quality) | Websites/discussion forums |
| ---------------------- | ------------------- |--------------------|
| [So, You Want to be a Cryptographer](https://www.schneier.com/crypto-gram/archives/1999/1015.html#SoYouWanttobeaCryptographer) - Bruce Schneier (Oct 1999) | [The Joy of Cryptography](https://joyofcryptography.com/) - Mike Rosulek | [CryptoHack](https://cryptohack.org/) |
| [Recommended skills for a job in cryptology](https://crypto.stackexchange.com/a/8444/87215) - Reid (May 2013)| [A Graduate Course in Applied Cryptography](https://toc.cryptobook.us/) - Dan Boneh and Victor Shoup | [Cryptopals](https://cryptopals.com/) |
| [Applied Cryptography Engineering](https://sockpuppet.org/blog/2013/07/22/applied-practical-cryptography/) - Thomas and Erin Ptacek "Matasano" (Jul 2013) | [Cryptography](https://www.i2m.univ-amu.fr/perso/david.kohel/pub/crypto.pdf) - David R. Kohel | [Cryptography.SE](https://crypto.stackexchange.com/) |
| [How Not to Learn Cryptography](http://esl.cs.brown.edu/blog/how-not-to-learn-cryptography/) - Seny Kamara (Nov 2014) | [A Course in Cryptography](https://www.cs.cornell.edu/courses/cs4830/2010fa/lecnotes.pdf) - Rafael Pass and Abhi Shelat | [Cryptography FM](https://www.cryptography.fm/) |
| [Cryptography and Mathematics](https://dl.acm.org/doi/10.1145/2730916) - Kristin Lauter's interview in XRDS: Crossroads, The ACM Magazine for Students (Mar 2015) | [Foundations of Cryptography](https://web.cs.ucla.edu/~rafail/PUBLIC/OstrovskyDraftLecNotes2010.pdf) - Rafail Ostrovsky | [r/crypto](https://www.reddit.com/r/crypto/) |
| [How I became a cryptographer](https://littlemaninmyhead.wordpress.com/2017/05/18/how-i-became-a-cryptographer/) and [why I left cryptography](https://littlemaninmyhead.wordpress.com/2017/10/23/why-i-left-cryptography/) - Scott Contini (May-Oct 2017) | [Introduction to Modern Cryptography](https://cseweb.ucsd.edu/~mihir/papers/br-book.pdf) - Mihir Bellare and Phillip Rogaway | [r/cryptography](https://www.reddit.com/r/cryptography/) |
| [How To Learn Cryptography as a Programmer](https://soatok.blog/2020/06/10/how-to-learn-cryptography-as-a-programmer/) - Soatok (Jun 2020) | [Introduction to Cryptography](https://www.cs.cmu.edu/~goyal/15356/lecture_notes.pdf) (direct links: [videos](https://youtube.com/playlist?list=PLI3cKEs5b6gvelkJnHf16r3ADhYvcQjdr) and [course webpage](https://www.cs.cmu.edu/~goyal/15356/)) - Vipul Goyal  | [CryptoClub](https://www.cryptoclub.org/) |
| [How to become a Security Engineer](https://www.coryhardman.com/2021/05/how-to-become-security-engineer.html) - Cory Hardman (May 2021) | [Cryptography Primitives and Protocols](https://www.kiayias.com/Aggelos_Kiayias/Introduction_to_Modern_Cryptography_files/Cryptograph_Primitives_and_Protocols.pdf) -  Aggelos Kiayias|[52 Things by Bristol Cryptography](https://bristolcrypto.blogspot.com/2014/10/52-things-number-1-different-types-of.html)  |
| [So, you want to be a Cryptographer?](https://gotchas.salusa.dev/GettingStarted.html) - Greg Rubin (May 2022) | [Proofs, Arguments, and Zero-Knowledge](https://people.cs.georgetown.edu/jthaler/ProofsArgsAndZK.html) - Justin Thaler | [SimonsTV](https://simons.berkeley.edu/videos)
| [Some Cryptography Books I Like](https://cronokirby.com/posts/2022/05/some-cryptography-books-i-like/) - Lúcás Meier (May 2022) | [Building Cryptographic Proofs from Hash Functions](https://snargsbook.org/) -  Alessandro Chiesa and Eylon Yogev | [Cryptology ePrint Archive](https://eprint.iacr.org/) |
| [The best books for cryptography apprentices](https://shepherd.com/best-books/for-cryptography-apprentices) - Jean-Philippe Aumasson (Jul 2022) | [Cryptography 101](https://cryptography101.ca/) - Alfred Menezes | [AskCrypto](https://askcryp.to/) |
| [The Cryptographer Designs Encryption that Even Quantum Hardware Can't Crack](https://ieeexplore.ieee.org/document/10824228) - Joppe Bos's interview in IEEE Spectrum Magazine (Jan 2025) | [Cryptography for Toddlers](https://www.cybok.org/media/downloads/Learning_Together_Cryptography_for_Toddlers.pdf) - Elizabeth A. Quaglia and Alex Thompson ([CyBOK](https://www.cybok.org/)) | [Post-Quantum signatures zoo](https://pqshield.github.io/nist-sigs-zoo/) |



## Computationally secure cryptography

<img align="right" width="350" height="220" src="https://imgs.xkcd.com/comics/security.png">

These cryptosystems are considered secure against the computation power offered by humans with pencil-paper, computers, and quantum computers.
* ### [Pencil-paper safe cryptography](https://gkorpal.github.io/pencil)
* ### [Classical computer safe cryptography](https://gkorpal.github.io/computer)
* ### [Quantum computer safe cryptography](https://gkorpal.github.io/quantum)


<!-----
<p>
<center>
<a href="https://xkcd.com/538/">
     <img alt="rsa" src="https://imgs.xkcd.com/comics/security.png" class="center">
</a>
</center>


<p>
<center>
<a href="https://dilbert.com/strip/2012-04-17">
     <img alt="Equality" src="https://assets.amuniversal.com/57d36e70e4f2012fed51001dd8b71c47" class="center"
           width="600" height="187">
</a>
</center>
</p>
</p>
 **Kerckhoffs's principle:** *A cryptosystem should be secure even if everything about the system, except the key, is public knowledge.*----->


## Unconditionally secure cryptography

<img style="display: block; margin: auto;" width="283" height="300" src="https://www.smbc-comics.com/comics/1544366826-20181209.png">

TODO: Quantum cryptography

# Math tech

The following is a list of various math tech setups I have worked with over the years.

|  Interval (years) | Operating system (user interface) | Primary software | 
| ----------------- | ---------------- |-------------|
| 2014 to 2019| Ubuntu (LXDE, GNOME 2, Unity, and Cinnamon) | TexMaker |
| 2019 to 2020| Debian (Crostini/Linux on ChromeOS) | TexMaker |
| 2020 to 2021| Fedora (Xfce and GNOME 3) | Vim+MuPDF |
| 2021 to 2023| openSUSE (KDE Plasma 5) | Vim+MuPDF |
| 2023 to 2025| Ubuntu (Windows Subsystem for Linux 2) | VSCode with LaTeX Workshop Extension | 

## Git

Git is a version control system that was developed to manage Linux development. I use GitHub as the remote server for my git repositories. Here is a tutorial to get started: [https://swcarpentry.github.io/git-novice/](https://swcarpentry.github.io/git-novice/)

Some other useful resources:
- Git Guides: [https://github.com/git-guides](https://github.com/git-guides)
- Git Cheatsheets: [https://training.github.com/](https://training.github.com/)
- GitHub for Mathematicians: [https://g4m.code4math.org/g4m.html](https://g4m.code4math.org/g4m.html)

## Markdown

Markdown is a markup language that was developed to bridge the gap between raw text and HTML. One can learn the basics here: [https://www.markdownguide.org/](https://www.markdownguide.org/)

There are different flavors that add various features:
- GitHub flavor ([kramdown](https://kramdown.gettalong.org/documentation.html) with support for  [math](https://github.blog/2022-05-19-math-support-in-markdown/), [flowchart](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/), and [footnote](https://github.blog/changelog/2021-09-30-footnotes-now-supported-in-markdown-fields/)): [https://docs.github.com/en/get-started/writing-on-github](https://docs.github.com/en/get-started/writing-on-github)
- Zettlr flavor (+[KaTeX](https://katex.org/)): [https://docs.zettlr.com/en/reference/markdown-basics/](https://docs.zettlr.com/en/reference/markdown-basics/)
- Quarto flavor ([Pandoc Markdown](https://kdheepak.com/blog/writing-papers-with-markdown/)): [https://quarto.org/docs/authoring/markdown-basics.html](https://quarto.org/docs/authoring/markdown-basics.html)
- Ghostwriter flavor ([CommonMark](https://commonmark.org/) et al.): [https://ghostwriter.kde.org/documentation/](https://ghostwriter.kde.org/documentation/)

## TeX

TeX is a typesetting system that was developed to meet the needs of mathematical and scientific typography. There are different flavors like [pdfTeX vs XeTeX vs LuaTeX](https://texfaq.org/FAQ-xetex-luatex), [LaTeX vs ConTeXt](https://texfaq.org/FAQ-context), and [BibTeX vs BibLaTeX](https://tex.stackexchange.com/questions/25701/bibtex-vs-biber-and-biblatex-vs-natbib). I use pdfTeX with BibTeX to produce PDF articles, reports, and presentations. Here is a tutorial to get started: [https://edbennett.github.io/latex-tutorial/](https://edbennett.github.io/latex-tutorial/)

Further readings:

|  LaTeX basics | Assistance tools | 
| ----------------- | ---------------- |
| [LaTeX guide](https://www.learnlatex.org/) | [Detexify](https://detexify.kirelabs.org/classify.html) | 
| [LaTeX typesetting game](https://texnique.xyz/) | [Equation editor](https://editor.codecogs.com/) | 
| [LaTeX cheat sheet](https://quickref.me/latex.html) | [Table generator](https://www.tablesgenerator.com/) | 
| [TikZ docs](https://tikz.dev/) | [TikZ-cd generator](https://q.uiver.app/)| 
| [BibLaTeX cheat sheet](https://tug.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf) | [JabRef browser extension](https://docs.jabref.org/collect/jabref-browser-extension) |
| [Beamer guide](https://latex-beamer.com/)| [Beamer themes](https://mpetroff.net/files/beamer-theme-matrix/) |


## Julia

Julia is a modern programming language that was developed to combine readability, speed, and scalability in one tool. It readily adopts cool features from other languages like [its amazing package manager](https://www.youtube.com/watch?v=HgFmiT5p0zU) `Pkg` inspired by Rust's `cargo`. One can learn the basics from this tutorial: [https://github.com/JuliaAcademy/JuliaProgrammingForNervousBeginners](https://github.com/JuliaAcademy/JuliaProgrammingForNervousBeginners)

If new to programming, consider solving some exercises from [CodeAbby](https://www.codeabbey.com/) or [Project Euler](https://projecteuler.net/).

Some other useful resources:

| Documentation | Packages |
| ------------- | ------- |
| [Style guide](https://docs.julialang.org/en/v1/manual/style-guide/) | [`Pluto`](https://computationalthinking.mit.edu) |
| [Performance tips](https://docs.julialang.org/en/v1/manual/performance-tips/) | [`Revise`](https://modernjuliaworkflows.org/) |
| [Unicode input](https://docs.julialang.org/en/v1/manual/unicode-input/) | [`Hecke`](https://github.com/thofma/HeckeTutorials.jl/blob/master/Performance.ipynb) |
| [Math operators](https://docs.julialang.org/en/v1/manual/mathematical-operations/) | [`Oscar`](https://www.oscar-system.org/tutorials/) |
| [Cheatsheet](https://cheatsheet.juliadocs.org/) | [`LaTeXStings`](https://m3g.github.io/JuliaNotes.jl/stable/figures/) |
| [Floating point math](https://0.30000000000000004.com/#julia) | [`Flux`](https://book.sciml.ai/) |

