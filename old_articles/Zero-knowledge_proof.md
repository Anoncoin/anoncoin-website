---
layout: old_page
title: Zero-knowledge proof
permalink: /Zero-knowledge_proof/
---

A **zero-knowledge proof** is a method by which one party can prove to another that a given statement is true, without conveying any additional information apart from the fact that the statement is indeed true. In the Zerocoin protocol, zero-knowledge proofs are used in the process of redeeming previously minted zerocoins for anoncoins. The proof shows that the party previously minted a zerocoin, without making known which zerocoin was minted.

Non Interactive Zero Knowledge Proof of Knowledge
-------------------------------------------------

A simple example of a zero-knowledge proof is the proof of knowledge of a discrete logarithm. Given an equation of the form


*y* = *g*<sup>*x*</sup> mod *q*

where the integers *y*, *g* and *q* are known, it is wished to prove knowledge of the discrete logarithm *x*. When *q* is a large prime number, the computation of the discrete logarithm is mathematically difficult, and no efficient solution exists. The proof of knowledge of *x* is here formulated in the framework of the multiplicative group of integers modulo *q*, **Z**<sub>*q*</sub>. The elements of the group *G* of order *q* are numerated from 0 to *q*-1, with *g*<sup>*q*</sup> = 1. When a value exceeds *q*, it is simply replaced with its value modulo *q*.

The proof that Zerocoin uses is a 'non-interactive proof' because the party provides all information necessary to verify the proof. This is in contrast to interactive proofs, where the verifier must send information to the party as part of a three-stage verification process. In mathematical notation, non-interactive zero-knowledge proofs of knowledge can be denoted as


NIZKPoK{(*x*), *h* = *g*<sup>*x*</sup>}

where all values not in parentheses are assumed known to the verifier.

Proof of knowledge of the discreet logarithm *x* can be proved without divulging its value using the following Schnorr protocol.

1.  Choose a random integer *r* between 0 and *q*-1.
2.  Calculate *t* = *g*<sup>*r*</sup>. This is referred to as the commitment.
3.  Compute the hash of *t*, *c* = *H*(*t*) mod *q*. (If a non-interactive proof were being used, the verifier would instead provide a random number *c*, and *c* would be the 'challenge'.)
4.  Calculate *s* = *xc* + *r* (mod *q*).
5.  The prover sends (*t*, *s*) to the verifier.
6.  The verifier accepts the proof if *g*<sup>*s*</sup> = *t* *y*<sup>*c*</sup>.

The last step is easily proved, since *g*<sup>*xc*\ +\ *r*</sup> = *g*<sup>*r*</sup> (*g*<sup>*x*</sup>)<sup>*c*</sup>. The probability of the party fooling the verifier that they know *x* is 1/*q*.

Application to Zerocoin
-----------------------

A zerocoin *c* is defined by the equation


*c* = *g*<sup>*S*</sup> *h*<sup>*r*</sup> mod *p*

where the integers *g*, *h*, and *p* are setup parameters known to all, and where the serial number *S* and random number *r* are known only to the owner of the coin. The coin *c* is a [Pedersen commitment](/Commitment_scheme "wikilink") that must be a prime number.

As part of the Zerocoin protocol, all of the coins are ['accumulated'](/Cryptographic_accumulator "wikilink") into the value *A* by an equation of the form


*A* = *u*<sup>c<sub>1</sub>\ c<sub>2</sub>\ c<sub>3</sub>\ ...\ c\ ...\ c<sub>n</sub></sup> (mod N)

where the integers *A*, *u* and *N* are known to everyone. The witness *w* of a coin *c* is defined as the accumulation of all coins with the exception of *c*


*w* = *u*<sup>c<sub>1</sub>\ c<sub>2</sub>\ c<sub>3</sub>\ ...\ c<sub>n</sub></sup> (mod N).

Given *A*, *w*, and *v*, it can be verified that the coin *v* was accumulated in *A* if


*A*' = *w*<sup>*v*</sup> mod *N* = *A*.

When this is satisfied, the function AccVerify((N,u),A,c,w) is set to unity.

To prove ownership of a Zerocoin, one must provide the serial number *S*, and prove knowledge of one coin *c* and the random number *r* used to generate the coin, without divulging the value of either. This is done by two separate zero-knowledge proofs, denoted schematically by the equation


NIZKPoK{(*c*, *w*, *r*), AccVerify((N,u),A,c,w) = 1, and *c* = *g*<sup>*S*</sup>*h*<sup>*r*</sup>}.

A [zero-knowledge proof](/Zero-Knowledge_Proof "wikilink") for knowledge of the coin *c* and witnesss *w* is given by Camenisch and Lysyanskaya (2002). The zero-knowledge proof for knowledge of *c* and *r* is given by Miers et al. (2013).

See also
--------

-   [Commitment scheme](/Commitment_scheme "wikilink")
-   [Cryptographic accumulator](/Cryptographic_accumulator "wikilink")

References
----------

Camenisch, J., and A. Lysyanskaya (2002). [Dynamic Accumulators and Application to Efficient Revocation of Anonymous Credentials](http://cs.brown.edu/people/anna/papers/camlys02.pdf), CRYPTO 2002, LNCS 2442, pp. 61–76.

Garman, C., M. Green, I. Miers, and A. D. Rubin (2013). Rational Zero: Economic Security for Zerocoin with Everlasting Anonymity. In: JHUDCS.

Goldreich, O., Micali, S., Wigderson, A.: Proofs that yield nothing but their validity and a methodology of cryptographic protocol design. In: FOCS (1986).

Goldwasser, S, S. Micali, and C. Rackoff (1985). The knowledge complexity of interactive proof-systems (extended abstract). In 17th Annual ACM Symposium on Theory of Computing (STOC'85), pages 291-304.

Miers, I., C. Garman, M. Green, A. D. Rubin (2013). \[<http://spar.isi.jhu.edu/~mgreen/ZerocoinOakland.pdf>| Zerocoin: Anonymous Distributed E-Cash from Bitcoin\], 2013 IEEE Symposium on Security and Privacy, IEEE Computer Society Conference Publishing Services, pp. 397-411, <doi:10.1109/SP.2013.34>.