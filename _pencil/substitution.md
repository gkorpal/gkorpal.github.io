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

Substitution is a function which uses a set of rules to transform elements of a sequence into a new sequence using a set of rules which "translate" from the original sequence to its transformation. 

The easiest substitution is given when each character is replaced by exactly one other character. This encryption can be broken with statistical methods because in every language characters appear with a particular probability. In this discussion we will work with English alphabets. We numerically encode the alphabets $\{A, B . . . , Z\}$ as the elements $\{0, 1, . . . , 25\}$ of $\mathbb{Z}/26\mathbb{Z}$. SageMath function:
`````python
def str2lst(s):
  return [ord(x)-65 for x in s] # since ASCII of A is 65

def lst2str(lst):
  return join([chr(int(x)+65) for x in lst])
`````

Let's see some popular examples:

* **Caesar cipher (shift cipher):**  This is a monoalphabetic substitution cipher. We obtain the ciphertext by replacing each letter of the message by the letter $n$ places beyond it in the normal alphabet. SageMath function:
`````python
def caesar(pl,n) :
  pln = str2lst(pl)
  pln2 = [(X+N)%26 for x in pln]
  return lst2str(pln2)
`````

For example, when $n=3$ and plaintext is "BEWARE OF ZOMBIES" we do
  * Delete spaces to get "BEWAREOFZOMBIES"
  * Replace each letter by the number to which it corresponds
  * Add 3 to each of these numbers and reduce each $\mod 26$.
  * Replace the resulting numbers by their letter equivalents in the letter-number correspondences to get ciphertext "EHZDUHRICRPELHV"

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
`````

* **Vigenere cipher:** This is a polyalphabetic substitution cipher. It has several Caesar ciphers in sequence with different shift values. Vigenère encryption $E$ using the key $K$ can be written as $C_{i}=E_{K}(M_{i})=(M_{i}+K_{i}) \pmod {26}$ and decryption $D$ using the key $K$ is $M_{i}=D_{K}(C_{i})=(C_{i}-K_{i}+26)\pmod {26}$ in which $M=M_{1}\dots M_{n}$ is the message, $C=C_{1}\dots C_{n}$ is the ciphertext and $K=K_{1}\dots K_{n}$ is the key obtained by repeating the keyword $\lceil n/m\rceil$ times in which $m$ is the keyword length. SageMath example:

`````python

`````

## References
<a id="1">[1]</a> G. Korpal, [Enigma Cryptanalysis]((https://gkorpal.github.io/files/summer2015-enigma_cryptanalysis-gaurish.pdf), July 2015.

<a id="2">[2]</a> David R. Kohel, [Cryptography](http://iml.univ-mrs.fr/~kohel/pub/crypto.pdf), July 2008.

<a id="2">[3]</a> David R. Kohel and Minh Van Nguyen, [Classical Cryptosystems](https://doc.sagemath.org/html/en/reference/cryptography/sage/crypto/classical.html), 2007-08.
