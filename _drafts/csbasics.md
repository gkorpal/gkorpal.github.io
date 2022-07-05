---
title: 'CS Basics'
date: 2021-10-02
tags:
  - problem-solving
---

Cypherpunks write code ([*A Cypherpunk's Manifesto* - Eric Hughes, 1993](https://www.activism.net/cypherpunk/manifesto.html)). Therefore, I want to work through the various problems from [Project Euler](https://projecteuler.net/) and [Cryptopals](https://cryptopals.com/). However, I can't code proficiently in any language.

## The past
In the past, I have dabbled into programming using different languages:

| Education level | Programming language | IDE/Editor (Operating System) |
| --------------- | -------------------- | ---------------------------- |
|Primary school (classes I to IV) | Logo | MSWLogo (Windows 98)|
|Middle school (classes V to VIII) | [Small Basic](https://github.com/gkorpal/DreamSpark-SmallBasic) | Microsoft Small Basic (Windows XP SP3)|
|High school (classes IX to XII) | [Swing (Java)/SQL](https://github.com/gkorpal/learning-Java_GUI) | NetBeans/MySQL (Windows 7)|
|Undergraduate school | [C++](https://github.com/gkorpal/learning-Cpp_OOP) |Code::Blocks (Ubuntu 14.04)|

Unfortunately, I never spent time on honing my programming skills. Therefore, at the beginning of my graduate school, I thought of properly learning [programming in Python](https://gkorpal.github.io/posts/2021/01/higher-arithmetic-computations/). However, most of the [study materials](https://github.com/gkorpal/learning-Python_maths) I found were more about "writing code to solve data science problems" rather than "learning to solve problems using programming."

## The present

I spent one year learning the basics of computer science following the advice from UArizona Computer Science department students and professors. None of the textbooks were read cover to cover.


| Topic | Textbook | Complementary Material | Supplementary Material |
|-------| -------- | -----------------------| -----------------------|
| Programming | How to Design Programs, by Felleisen, Findler, Flatt, and Krishnamurthi (2nd edition) |  [HTML edition](https://htdp.org/2022-2-9/Book/index.html); [Racket](https://racket-lang.org/); Northeastern CS 2500 lecture [notes](https://course.ccs.neu.edu/cs2500/syllabus.html) and [videos](https://www.ccs.neu.edu/home/nderbinsky/fundies1/); Program by Design [resources](https://programbydesign.org/materials); UBC CPSC 110 [resources](http://cs110.students.cs.ubc.ca/syllabus.html) | Structure and Interpretation of Computer Programs, by Abelson, Sussman, and Sussman ([Wizard book](https://mitpress.mit.edu/sites/default/files/sicp/index.html), [PDF edition](https://github.com/sarabander/sicp-pdf), Brian Harvey's lecture [notes](https://people.eecs.berkeley.edu/~bh/61a-pages/) and [videos](https://archive.org/details/ucberkeley-webcast-PL3E89002AA9B9879E)); Harvard [CS 50](https://cs50.harvard.edu/x/); UC Berkeley CS 61A lecture [notes](https://composingprograms.com/)|
| Algorithms | Introduction to Algorithms, by Cormen, Leiserson, Rivest, and Stein (3rd edition) | [Online Resources](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) | Algorithm Design, by Kleinberg, and Tardos ([slides](https://www.cs.princeton.edu/~wayne/kleinberg-tardos/)); Algorithms, by Sedgewick and Wayne; Stanford CS 161 lecture [videos](https://www.youtube.com/channel/UCH4s4ek5zqNvct5oy9_jd_g/featured); UC Berkeley CS 61B lecture [notes](https://inst.eecs.berkeley.edu/~cs61b)|
| Systems | The Elements of Computing Systems, by Nisan and Schocken (2nd edition) | [Nand2Tetris](https://www.nand2tetris.org/); Object-Oriented Programming with [Java](https://java-programming.mooc.fi/) or [Python](https://programming-22.mooc.fi/)| Computer Systems: A Programmer's Perspective, by Bryant and O'Hallaron ([online resources](https://csapp.cs.cmu.edu/3e/home.html)); Computer Organization and Design, by Patterson and Hennessy; Basics of Compiler Design, by Mogensen ([PDF edition](http://hjemmesider.diku.dk/~torbenm/Basics/index.html)); Modern Compiler Implementation in ML, by Appel ([Tiger book](https://www.cs.princeton.edu/~appel/modern/ml/)); Crafting Interpreters, by Nystrom ([HTML edition](https://craftinginterpreters.com/contents.html)); UC Berkeley CS 61C lecture [notes](https://inst.eecs.berkeley.edu/~cs61c/sp15/) and [videos](https://archive.org/details/ucberkeley-webcast-PL-XXv-cvA_iCl2-D-FS5mk0jFF6cYSJs_) |
| Networking | Computer Networks: A Systems Approach, by Peterson and Davie (5th edition) | [HTML edition](https://book.systemsapproach.org/index.html); C Programming: A Modern Approach, by King (2nd edition) ([my notes](https://github.com/gkorpal/learning-C_systems)); [Mininet](https://github.com/mininet/mininet/wiki/Teaching-and-Learning-with-Mininet)| Computer Networking: A Top-Down Approach, by Kurose and Ross ([videos](http://gaia.cs.umass.edu/kurose_ross/online_lectures.htm) and [Wireshark labs](https://gaia.cs.umass.edu/kurose_ross/wireshark.php)); Stanford CS 144 lecture [notes](https://cs144.github.io/) | 
| Security | Computer Security: Principles and Practice, by Stallings and Brown (4th edition) | Network Security: Private Communication in a Public World, by Kaufman, Perlman and Speciner; [SEEDLabs](https://seedsecuritylabs.org/) | Security in Computing, by Pfleeger and Pfleeger; Security Engineering, by Anderson ([drafts](https://www.cl.cam.ac.uk/~rja14/book.html)); UC Berkeley CS 161 lecture [notes](https://textbook.cs161.org/)|
| Theory | Introduction to the Theory of Computation, by Sipser (3rd edition) | MIT OCW 18.404J lecture [notes](https://ocw.mit.edu/courses/18-404j-theory-of-computation-fall-2020/pages/lecture-notes/) and [videos](https://www.youtube.com/playlist?list=PLUl4u3cNGP60_JNv2MmK3wkOt9syvfQWY) | Introduction to Automata Theory, Languages, and Computation, by Hopcroft, Motwani, and Ullman; Computability and Logic, by Boolos, Burgess, and Jeffrey; The Nature Of Computation, by Moore and Mertens; CMU CS 251 lecture [notes](https://www.cs251.com/Text.html) and [videos](https://youtube.com/playlist?list=PLKzLTB8HeSUIuln-o1mbXfTr8HmIhiGEg)|

During this one year journey, I got the opportunities to practice programming using Racket ([Beginning Student Language](https://github.com/gkorpal/HtDP)), C ([Software Router](https://github.com/gkorpal/SoftwareRouter) and [TLS VPN](https://github.com/gkorpal/TLS-VPN)), and Python3 ([Jack VM](https://github.com/gkorpal/Nand2Tetris)). I also learned regular expression usage in AWK ([Frequency Analysis](https://github.com/gkorpal/TLS-VPN/tree/master/practice/secret-key_encryption)) and Python ([Lexical Analysis](https://github.com/gkorpal/Nand2Tetris/tree/master/p10p11)).

## The future
Next, I would like to improve my Python and C programming skills by 
- solving the exercises from [Project Euler](https://projecteuler.net/) and [Cryptopals](https://cryptopals.com/);
- contributing to [Open Source projects](https://www.firsttimersonly.com/), especially [SageMath](https://doc.sagemath.org/html/en/faq/faq-contribute.html);
- creating programming projects related to my thesis

However, there are [many more programming languages](https://en.wikipedia.org/wiki/History_of_programming_languages) to choose from. For example, following are some of the main programming languages developed before the Internet age (source: Programming Languages - Principles and Practice, by Louden & Lambert, 3rd ed)

<img align="center" width="600" height="350" src="/images/timeline.png">

Eventually, I would also like to learn Rust, and participate in Capture The Flag (CTF) competitions like [CrytoHack](https://cryptohack.org/), [TryHackMe](https://tryhackme.com/) and [HackTheBox](https://www.hackthebox.com/) (Kali Linux).


<!---- 
Longterm goals (post-PhD):

| Topic | Textbook | Complementary Material | Supplementary Material |
|-------| -------- | -----------------------| -----------------------|
| Operating Systems | Operating Systems: Three Easy Pieces, by Arpaci-Dusseau and Arpaci-Dusseau | [PDF edition](https://pages.cs.wisc.edu/~remzi/OSTEP/); Mythili Vutukuru's [lectures](https://www.cse.iitb.ac.in/~mythili/os/) | Operating System Concepts, by Silberschatz, Galvin, and Gagne ([Dinosaur book](https://codex.cs.yale.edu/avi/os-book/OS10/index.html)) |
|Compilers | Modern Compiler Implementation in ML, by Appel | [Tiger book](https://www.cs.princeton.edu/~appel/modern/ml/); Crafting Interpreters, by Nystrom ([HTML edition](https://craftinginterpreters.com/contents.html)); [Why learn compiler design](https://www2.cs.arizona.edu/classes/cs453/fall15/DOCS/teaching_compilers.pdf); [Haskell compiler](https://crypto.stanford.edu/~blynn/compiler/); [Lex & Yacc](http://dinosaur.compilertools.net/) | Engineering a Compiler, by Cooper and Torczon (2nd edition); Basics of Compiler Design, by Mogensen ([PDF edition](http://hjemmesider.diku.dk/~torbenm/Basics/index.html)); ; Compilers: Principles, Techniques, and Tools, by Aho, Lam, Sethi and Ullman ([Dragon book](https://suif.stanford.edu/dragonbook/))|

[this discussion](https://cstheory.stackexchange.com/questions/3253/what-books-should-everyone-read) 
<!---- 
|Cryptography| Foundations of cryptography vol 1 and 2, by Oded Goldreich | complexity theory | modern text and online notes | 
Problem Solving with Algorithms and Data Structures using Python, by Miller and Ranum ([HTML edition](https://runestone.academy/ns/books/published/pythonds/index.html)); Introduction to Algorithms by Manber;

---->
