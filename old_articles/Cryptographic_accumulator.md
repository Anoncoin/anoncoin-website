---
layout: old_page
title: Cryptographic accumulator
permalink: /Cryptographic_accumulator/
---

**One-way cryptographic accumulators** allow parties to combine many elements into a constant-sized data structure. This structure allows one to prove efficiently that a specific value is contained within the set, without disclosing the value of the member. In [Zerocoin](/Zerocoin "wikilink"), the network computes an accumulator *A* over all coin commitments (c<sub>1</sub>, ...., c<sub>n</sub>), along with the appropriate membership witnesses for each item in the set. The witness is simply the accumulator of all coins with the exception of one, and during a zerocoin spend transaction, the user needs to prove knowledge of one such witness.

Zerocoin accumulator
--------------------

The accumulators used in zerocoin have the following properties:

-   The accumulator and its associated witnesses are publicly computable and verifiable with no trusted parties.
-   The accumulator binds the computing party to the values in the set.
-   The accumulator supports an efficient zero-knowledge proof of set membership.

The Zerocoin accumulator is defined as


A = u<sup>c<sub>1</sub>\ c<sub>2</sub>\ c<sub>3</sub>\ ...\ c\ ...\ c<sub>n</sub></sup> (mod N)

where the integers *A*, *u* and *N* are known to everyone. The coin *c* is a prime number that is a [Pedersen commitment](/Commitment_scheme "wikilink") of a coin serial number *S* and random number *r*. The witness *w* of a coin *c* is defined as the accumulation of all coins with the exception of *c*


w = u<sup>c<sub>1</sub>\ c<sub>2</sub>\ c<sub>3</sub>\ ...\ c<sub>n</sub></sup> (mod N).

For computational efficiency, it is noted that the accumulator can be updated incrementally with a new value *x* by the equation


A<sub>n+1</sub> = A<sub>n</sub><sup>x</sup> (mod N).

Given *A*, *w*, and *v*, it can be verified that the coin *v* was accumulated in *A* if


A' = w<sup>v</sup> mod N = A.

A [zero-knowledge proof](/Zero-Knowledge_Proofs "wikilink") for knowledge of the coin *c* and witnesss *w* is given by Camenisch and Lysyanskaya (2002).

See also
--------

-   [Zero-knowledge proof](/Zero-knowledge_proof "wikilink")

References
----------

Benaloh, J., and M. de Mare (1994). [One-way accumulators: a decentralized alternative to digital signatures](http://www.cs.stevens.edu/~mdemare/pubs/owa.pdf), in EUROCRYPT ’93, vol. 765 of LNCS, pp. 274–285.

Camenisch, J., and A. Lysyanskaya (2002). [Dynamic Accumulators and Application to Efficient Revocation of Anonymous Credentials](http://cs.brown.edu/people/anna/papers/camlys02.pdf), CRYPTO 2002, LNCS 2442, pp. 61–76.