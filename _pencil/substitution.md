---
title: "Substitution Ciphers"
collection: pencil
permalink: /pencil/substitution
excerpt:
date: 2021-08-29
venue: 
paperurl: 
citation: 
---

**Substitution** is a function which uses a set of rules to transform elements of a sequence into a new sequence using a set of rules which "translate" from the original sequence to its transformation. The easiest substitution is given when each character is replaced by exactly one other character. This encryption can be broken with statistical methods because in every language characters appear with a particular probability. 

In this discussion we will work with English alphabets. We numerically encode the alphabets $\{A, B . . . , Z\}$ as the elements $\{0, 1, . . . , 25\}$ of $\mathbb{Z}/26\mathbb{Z}$. SageMath function:

`````python
sage: def str2lst(s): 
....:     return [ord(x)-65 for x in s] 

sage: def lst2str(lst): 
....:     return ''.join([chr(int(x)+65) for x in lst])  # join without space
`````

Let's see some popular examples:

* **Caesar cipher (shift cipher):**  This is a monoalphabetic substitution cipher. We obtain the ciphertext by replacing each letter of the message by the letter $n$ places beyond it in the normal alphabet. SageMath function:

`````python
sage: def caesar(pl, n): 
....:     pln = str2lst(pl) 
....:     pln2 = [(x+n)%26 for x in pln] 
....:     return lst2str(pln2)
`````

For example, when $n=3$ and message is "BEWARE OF ZOMBIES" we get plain text by deleting spaces "BEWAREOFZOMBIES", and then we can use the above function:

`````python
sage: pl = 'BEWAREOFZOMBIES'                                                                                         
sage: n = 3                                                                                                          
sage: caesar(pl, n)                                                                                                  
'EHZDUHRICRPELHV'
`````

* **Affine cipher:** This is direct generalization of Caesar cipher. Let $x$ be the numeric encoding of the alphabet. Then we obtain the ciphertext by applying the transformation of the form $x \mapsto ax + b$, for any $a$ coprime to 26. Thus, the Caesar cipher is an Affine cipher with $a = 1$. SageMath example:

`````python
sage: A = AffineCryptosystem(AlphabeticStrings())                                                               
sage: A                                                                                                              
Affine cryptosystem on Free alphabetic string monoid on A-Z
sage: P = A.encoding("Beware of Zombies")                                                                            
sage: P                                                                                                              
BEWAREOFZOMBIES
sage: a,b = (1,3)                                                                                                    
sage: C = A.enciphering(a,b,P)                                                                                       
sage: C                                                                                                              
EHZDUHRICRPELHV
sage: A.deciphering(a, b, C) == P
True
`````

* **Vigenere cipher:** This is a polyalphabetic substitution cipher. It has several Caesar ciphers in sequence with different shift values. Vigenère encryption $E$ using the key $K$ can be written as $C_{i}=E_{K}(M_{i})=(M_{i}+K_{i}) \pmod {26}$ and decryption $D$ using the key $K$ is $M_{i}=D_{K}(C_{i})=(C_{i}-K_{i}+26)\pmod {26}$ in which $M=M_{1}\dots M_{n}$ is the message, $C=C_{1}\dots C_{n}$ is the ciphertext and $K=K_{1}\dots K_{n}$ is the key obtained by repeating the keyword $\lceil n/m\rceil$ times in which $m$ is the keyword length. SageMath function:

`````python
sage: def vige(s,k): 
....:     pn = len(s) 
....:     kn = len(k) 
....:     pl = str2lst(s) 
....:     kl = str2lst(k) 
....:     cl = [mod(pl[i]+kl[mod(i,kn)],26) for i in range(pn)] # to decipher subtract from ciphertext
....:     return lst2str(cl) 
`````

For example, for the message "Beware of Zombies" and key "elephant" we get
`````python
sage: s = 'BEWAREOFZOMBIES'                                                                                          
sage: k = 'ELEPHANT'                                                                                                 
sage: vige(s,k)                                                                                                      
'FPAPYEBYDZQQPEF'
`````

SageMath example:

`````python
sage: A = AlphabeticStrings()                                                                                        
sage: M = A.encoding("Beware of Zombies")                                                                            
sage: K = A.encoding("ELEPHANT")  
sage: V = VigenereCryptosystem(AlphabeticStrings(), len(K))                                                          
sage: E = V.enciphering(K,M)                                                                                         
sage: E                                                                                                              
FPAPYEBYDZQQPEF
sage: V.deciphering(K,E) == M                                                                                        
True
`````

If the message is shorter than the key, then the Vigenere cipher is essentially the **one-time pad**, which is unbreakable for a random key. If the key is not random, then you may get some information on the plaintext.

* **Playfair cipher:** This is a polygraphic substitution cipher in which pairs of letters are substituted (digraphic). In this the plaintext is broken up into two-letter digraphs with some restrictions. Those digraphs are encrypted using a **Polybius square**, (i.e. a 5x5 grid in which each letter of the alphabet is its own entry with the exception of I/J which are placed together). The positions of the letters in the digraph determine how the digraph is encrypted.

`````python
sage: def polybius(key): 
....:     alph = 'ABCDEFGHIKLMNOPQRSTUVWXYZ' # no J 
....:     pf = '' 
....:     for ch in key: 
....:         if (ch!= "J") & (pf.find(ch)==-1): 
....:             pf+=ch 
....:     for ch in alph: 
....:         if pf.find(ch)==-1: 
....:             pf+=ch 
....:     square = [[pf[5*i+j] for j in range(5)] for i in range(5)] 
....:     return square
....:
sage: def digraph(pl): 
....:     tmp = pl.replace('J', 'I') # replace J's with I's 
....:     n = len(tmp) 
....:     i = 0 
....:     while (n > 0) & (2*i+1 < len(tmp)): 
....:         if tmp[2*i] == tmp[2*i+1]: 
....:             tmp = insert('X', tmp, 2*i+1) # if both letters are the same add an uncommon letter like "X" after the first letter.
....:             n-=1 
....:             i+=1 
....:         else: 
....:             n-=2 
....:             i+=1 
....:     if len(tmp)%2 == 1: 
....:         tmp += 'X' # if only one letter is left, add an uncommon letter like "X"
....:     return tmp
....:
sage: def digraph_en(di, square): 
....:     for i in range(5): 
....:         for j in range(5): 
....:             if square[i][j] == di[0]: 
....:                 i0 = i 
....:                 j0 = j 
....:             if square[i][j] == di[1]: 
....:                 i1 = i 
....:                 j1 = j 
....:     if (i0 != i1) & (j0 != j1): 
....:         return square[i0][j1] + square[i1][j0]  # if the letters are not on the same row or column
....:     if (i0 == i1) & (j0 != j1): 
....:         return square[i0][(j0+1)%5] + square[i1][(j1+1)%5] # if the letters are in the same row, replace them with the letters to their immediate right 
....:     if (i0 != i1) & (j0 == j1): 
....:         return square[(i0+1)%5][j0] + square[(i1+1)%5][j1] # if the letters are in the same column, replace them with the letters immediately below
....:
sage: def playfair(pl, key): 
....:     square = polybius(key) 
....:     di = digraph(pl) 
....:     tmp = '' 
....:     for i in range(len(di)//2): 
....:         tmp += digraph_en(di[2*i]+di[2*i+1], square) 
....:     return tmp 
`````

Then, for (encoded) plain text "BEWAREOFZOMBIES" and key "ELEPHANT" we wii get:

`````python
sage: playfair("BEWAREOFZOMBIES","ELEPHANT")                                                                         
'NPZLOPVOVUIDFPRY'
`````
To decrypt, use the inverse (opposite) of the last 3 rules of `digraph_en` to get `digraph_de`, then drop any extra "X"s that do not make sense in the final message when finished. 

Another polygraphic substitution cipher is the **Hill cipher**. It uses matrix algebra for encryption/decryption. However, encryption is very difficult to perform by hand for any sufficiently large block size.

## References
1. G. Korpal, [Enigma Cryptanalysis](https://gkorpal.github.io/files/summer2015-enigma_cryptanalysis-gaurish.pdf), July 2015.

2. David R. Kohel, [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf), July 2008.

3. David R. Kohel and Minh Van Nguyen, [Classical Cryptosystems](https://doc.sagemath.org/html/en/reference/cryptography/sage/crypto/classical.html), SageMath reference manual, 2007--08.

4. A. Feaver et. al., [Sage Interactions - Cryptography](https://wiki.sagemath.org/interact/cryptography), SageMath Wiki, August 2019.

5. S. Tengely, [Lectures on Cryptography](http://shrek.unideb.hu/~tengely/crypto/webwork-mini.html), University of Debrecen, 2020.

6. A. McAndrew, Introduction to Cryptography with Open-Source Software, CRC Press, 2011.
