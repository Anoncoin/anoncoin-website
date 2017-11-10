---
layout: old_page
title: Commitment scheme
permalink: /Commitment_scheme/
---

A **commitment scheme** allows one to commit to a chosen value while keeping it hidden to others, with the ability to reveal the committed value later. Commitment schemes are designed so that a party cannot change the value after they have committed to it: that is, commitment schemes are binding. In Zerocoin commitment schemes are used to bind a serial number to a zerocoin.

Zerocoin coin commitments
-------------------------

As an example of a binding commitment, consider the following scenario. Pick a secret value *x* to commit from 0 to *p*−1, where *p* is a large prime number, calculate


c = g<sup>x</sup> (mod p)

and publish the value *c*. The discrete logarithm problem dictates that it is computationally infeasible to compute *x* from *c* when *p* is large and the integer *g* is known. In addition, it is not feasible to find another value of *x* that would give the same number *c*, so the scheme is binding. By providing the number *x*, anyone can easily verify that the equation gives the correct value of *c*.

A different example of a perfectly binding commitment scheme is the *Pedersen commitment*, which is what is used to bind a serial number *S* to a zerocoin *c*. This commitment is given as


c = g<sup>S</sup> h<sup>r</sup> (mod p).

In this equation, the integers *g* and *h*, as well as the prime number *p* are known to all parties. The user chooses two integers *S* and *r*, and then publishes the value *c*. Neither *S* nor *r* can be calculated from *c*, even if one of the two were to be provided. If a serial number *S* of a coin is published, ownership of the coin can be proved only by providing the number *r*. For the Zerocoin [cryptographic accumulator](/Cryptographic_accumulator/ "wikilink") to work correctly, the value *c* must be a prime number.

See also
--------

-   [Cryptographic accumulator](/Cryptographic_accumulator/ "wikilink")
-   [Zero-knowledge proof](/Zero-knowledge_proof/ "wikilink")