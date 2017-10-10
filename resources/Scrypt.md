---
layout: page
title: Scrypt
permalink: /Scrypt/
---

*Scrypt* is a password-based key derivation function and the algorithm was specifically designed to make it costly to perform large-scale custom hardware attacks by requiring large amounts of memory. In [Anoncoin](/Anoncoin "wikilink"), scrypt is the proof-of-work algorithm that miners use to compete to add blocks to the block chain.

Anoncoin parameters to call scrypt
----------------------------------

Anoncoin uses the same values as Litecoin for the call to scrypt as follows:

-   N = 1024;
-   r = 1;
-   p = 1;
-   salt is the same 80 bytes as the input
-   output is 256 bits (32 bytes)

Scrypt Hashing
--------------

The source code in C++ for the scrypt hashing function can be found here: [scrypt.cpp](https://github.com/Anoncoin/anoncoin/blob/master/src/scrypt.cpp)

[Category:Anoncoin](/Category:Anoncoin "wikilink")