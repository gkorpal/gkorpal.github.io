---
title: "Transposition Ciphers"
collection: pencil
permalink: /pencil/transposition
excerpt:
date: 2021-09-19
venue: 
paperurl: 
citation: 
---
 
Permutation of a set $X$ is a bijective function $\sigma : X \to X$ that for each element $x \in X$ assigns a unique value $\sigma(x) \in X$. A **transposition** is a permutation of two elements and any permutation is also a product of transpositions.

In most cases of transposition ciphers, the resulting permutation consists of several cycles with no particular relation between their lengths. The total number of letters represented in these cycles is less than the length of the message by the number of letters whose positions are unchanged, i.e. are in cycles consisting of just one number.

Let's see some popular examples:

* **Rail fence cipher (zigzag cipher):** In this the plaintext is written downwards diagonally on successive $n$ "rails" of an imaginary fence, then moving up when the bottom rail is reached, down again when the top rail is reached, and so on until the whole plaintext is written out. The ciphertext is then read off in rows. SageMath function:

`````python
sage: def zigzag(pl, key):
....:     rail = [[ '\n' for i in range(len(pl))] for j in range(key)] 
....:     # finding direction of flow 
....:     dir_down = False 
....:     row, col = 0,0 
....:     for i in range(len(pl)): 
....:         if (row == 0) or (row == key - 1): 
....:             dir_down = not dir_down 
....:         rail[row][col] = pl[i] 
....:         col += 1 
....:         if dir_down: 
....:             row += 1 
....:         else: 
....:             row -= 1 
....:     tmp = [] 
....:     for i in range(key): 
....:         for j in range(len(pl)): 
....:             if rail[i][j] != '\n': 
....:                 tmp.append(rail[i][j]) 
....:     return(''.join(tmp))
`````

Now, consider the example when $n=3$:

`````python
sage: zigzag("BEWAREOFZOMBIES", 3)                                                                                   
'BRZIEAEFOBEWOMS'
`````

Decryption is a bit [tricky](https://en.wikipedia.org/wiki/Rail_fence_cipher#Decryption).

* **Bifid cipher:** This is a fractionating transposition cipher. Breaking up or fractionating letters before moving them around improves the security of a cipher considerably. SageMath function:

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
....:     return pf # writing the square as a sequence read from left to right
....:
sage: def bifid(pl, key): 
....:     n = len(pl) 
....:     pairs = [] 
....:     ks = polybius(key) 
....:     for x in pl: 
....:         kx = ks.index(x) 
....:         pairs += [[kx//5,kx%5]] # getting the coordinates in polybius square
....:     tmp = flatten([x[0] for x in pairs]+[x[1] for x in pairs]) 
....:     ct = '' 
....:     for i in range(n): 
....:         pair=[tmp[2*i],tmp[2*i+1]] 
....:         ct += ks[5*pair[0]+pair[1]] 
....:     return ct                                                                                                            
`````

For example, if (encoded) plain text is "BEWAREOFZOMBIES" and key is "ELEPHANT" then

`````python
sage: bifid("BEWAREOFZOMBIES","ELEPHANT")                                                                            
'NVORYGFRLXEAAIH'
`````
For decryption apply the above steps in reverse.

`````python
sage: def bifid_de(ct, key): 
....:     n = len(ct) 
....:     pairs = [] 
....:     ks = polybius(key) 
....:     for x in ct: 
....:         kx = ks.index(x) 
....:         pairs += [[kx//5, kx%5]] 
....:     tmp = flatten(pairs) # len(tmp) = 2n
....:     A = tmp[:n] 
....:     B = tmp[n:] 
....:     pl = '' 
....:     for i in range(n): 
....:         pair = [A[i], B[i]] 
....:         pl += ks[5*pair[0]+pair[1]] 
....:     return pl 
....:                                                                                                             
sage: bifid_de("NVORYGFRLXEAAIH", "ELEPHANT")                                                                        
'BEWAREOFZOMBIES'
`````

**ADFGX cipher** is another example of a fractionating transposition cipher, which uses two keys (transposition key and fractionation key). It is named after the five letters used in the ciphertext: A, D, F, G and X. These letters were chosen in a way to reduce the possibility of operator error, as they are very different from each other when transmitted via morse code.

## References
1. G. Korpal, [Enigma Cryptanalysis](https://gkorpal.github.io/files/summer2015-enigma_cryptanalysis-gaurish.pdf), July 2015.

2. S. Tengely, [Lectures on Cryptography](http://shrek.unideb.hu/~tengely/crypto/webwork-mini.html), University of Debrecen, 2020.

3. A. McAndrew, Introduction to Cryptography with Open-Source Software, CRC Press, 2011.

4. P. Somwanshi, [Python3 program to illustrate Rail Fence Cipher Encryption and Decryption](https://www.geeksforgeeks.org/rail-fence-cipher-encryption-decryption/), GeeksforGeeks.
