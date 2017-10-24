---
layout: old_page
title: RSA UFO
permalink: /RSA_UFO/
---

When a [zerocoin](/zerocoin "wikilink") is minted, the coin is added as a member to the set of all zerocoins by way of a one-way [cryptographic accumulator](/cryptographic_accumulator "wikilink"). In order to prove later that a given zerocoin belongs to this set, during the initial setup of the accumulator, it is necessary to define a number N (or a set of such numbers) that is the product of at least two distinct prime numbers; this number becomes the accumulator modulus for the Zerocoin implementation. If the prime numbers are large enough, it would be infeasible for any party to factor N. However, any entity that knows all the factors would be able to bypass the security of the system and forge zerocoin membership proofs; it is impossible to verify that the factors were not saved by the generating party after multiplying together to form N. Anoncoin solves this setup problem by using RSA UFOs (generalized **RSA** moduli of **u**nknown complete **f**act**o**rization) for the accumulator moduli which can be generated in a trustless manner, meaning there is never a time when the factors are known to any party; the setup does not require any trusted third parties.

Sander's RSA UFO idea, and proof of security
--------------------------------------------

Sander's 1999 paper “Efficient Accumulators Without Trapdoor” describes a procedure for generating a number such that with probability p it has at least two distinct prime factors that are each at least k bits in size, where p and k can be chosen to be high enough to meet security needs. The general approach is to pick a public secure number source that is verifiably random and use it to generate a series of integers a<sub>i</sub> of bit size approximately 3\*k. In this paper, Sander proves that the probability of each of these integers a<sub>i</sub> having at least two such prime factors is a constant independent of the k chosen (in fact, this constant probability is about 0.16). To produce the final RSA UFO, the integers a<sub>i</sub> are multiplied together.

The number of integers depends on the chosen probability p. For example, if p is chosen to be (1 - 10^-9) (meaning there is a one in a billion chance of being insecure) and k is chosen to be 1024 bits (meaning the resulting RSA UFO has to have at least two distinct prime factors of at least 1024 bits each), then L = log (1-p) / log (1 - 0.16) ~ 119 integers a<sub>i</sub> are required. The total bit length of the resulting RSA UFO is roughly 3\*k\*L ~ 3\*1024\*119 = 365568 bits.

Anoncoin's improvements on the Sander RSA UFO concept
-----------------------------------------------------

Since it is completely impractical to have a 365000-bit accumulator modulus for Zerocoin, the Anoncoin project found it necessary to make two changes to Sander's RSA UFO concept. The first change is to skip the multiplication step at the end and have *multiple accumulator moduli*, requiring a coin to be accumulated in all of them to be valid; this has equivalent security but much greater efficiency and allows parallel calculation.

The second change is to find ways of increasing the constant probability from 0.16 to a value much closer to 1, which allows a smaller L value for the same probability p. It turns out that a large portion of 3072 bit numbers are secure against factorization despite not having at least two distinct prime factors of at least 1024 bits each (meaning it's erroneously considered to be insecure by the security definition in the Sander paper). For example, a 3072 bit number is secure against factorization if it has three distinct prime factors of 768 bits each, and no larger prime factors. The reason this is the case is because the two algorithms useful for factoring large randomly chosen numbers (the Elliptic Curve Method (ECM) and the General Number Field Sieve (GNFS)) increase in difficulty in very different ways: ECM's difficulty increases with the size of the factor to find, while GNFS's difficulty increases with the total size of the number to factor. Therefore, we can pick a new definition of security for each of our integers a<sub>i</sub>: the integer is secure if, after removing all prime factors less than 768 bits in size, the result is composite and greater than 2048 bits in size. To see why these numbers were chosen, consider that the largest factors publicly found by ECM are about 275 bits (which is vastly easier than finding 768 bit factors), and the largest number publicly factored by GNFS is 768 bits in size (which is vastly easier than factoring a 2048 bit number).

Using Monte Carlo simulations, the Anoncoin project found that if the size of the integers a<sub>i</sub> is increased to 3840 bits (which was chosen because Zerocoin performance sharply degrades for larger sizes) and if small prime factors up to roughly 150 bits in size are searched for by ECM (replacing any integers a<sub>i</sub> whose bit lengths are reduced by more than 10%, or that are completely factored), then the probability of the new security definition (above) being true is about 0.8; this is a significant improvement on Sander's probability of 0.16. Although a proof was not yet found due to being substantially more complex than Sander's security definition, the Anoncoin project is confident that an expert number theorist can place provable bounds on the probability that will confirm the 0.8 estimate.

The result is that L = 13 integers are needed, each with 3840 bits. For the secure and verifiably random number source, Sander proposed generating it from NYSE or Nasdaq ticker data at noon of a day chosen by U.S Congress; this is publicly verifiable and cannot be manipulated by a malicious party, at least not without tremendous difficulty. The Anoncoin project found it to be more expedient to generate the integers from the digits of a cryptographically secure hash function such as SHA-256. This means that anyone can verify that the Anoncoin project did not chose the integers a<sub>i</sub>, since doing that would require finding an input to SHA-256 that would generate a particular output (a “pre-image attack”), which is widely believed to be essentially impossible.

Generation of RSA UFOs
----------------------

As part of the RSA UFO selection to meet Anoncoin's security definition for an integer (see above), all small prime factors less than roughly 165 bits were removed from the RSA UFOs using the Elliptic Curve Method of factorization (ECM), which helps decrease the computational cost of Zerocoin operations; this distributed factorization project was called the “UFO project”; it lasted about 75 days, with a total of 8 core-years spent factoring in those 75 days. By removing small factors, the bit length of the number N decreases; if after removing small factors the bit length is smaller than a critical value of about 3456 bits (90% of 3840 bits), or if the remaining number is a prime (which means the UFO candidate has been completely factorized), the RSA UFO is discarded, and another one is generated. The results of the UFO project are discussed [here](https://bitcointalk.org/index.php?topic=227287.msg8855999#msg8855999).

On startup all Anoncoin wallet software deterministically generates the raw UFOs using hashing. The small factors found during the UFO project are then removed from the raw UFOs. (It would have been more efficient to have the final UFOs encoded directly in the software, but that would have the disadvantage of being less verifiable by code reviewers.) So the procedure to generate the complete RSA UFOs is 1) create the 13 “raw” UFOs by hashing, and 2) divide out the small factors found in the UFO project. If the RSA UFO bit length after division by small factors is lower than 3456, the UFO is discarded and the next UFO is generated, to bring the total number of UFO candidates back up to 13. Out of the 13 starting UFOs with index 0-12, we rejected UFOs with indices 5 and 7 because they were completely factorized, and rejected the UFO with index 13 because the bit length dropped below the 3456 bit threshold; as a result, three more UFOs were added to set being factorized (those with indices 13-15). The end result is that we had 13 UFOs with index 0 through 15 except 5, 7, and 13. This same process was performed identically and deterministically by the UFO clients and UFO server, and, after Zerocoin is released, by all Anoncoin wallets (except that wallets use only the factors found in the UFO project, and do not perform any factorization).

The [client source code](https://github.com/Anoncoin/ufo_client) and [server source code](https://github.com/Gnos1s/ufo_server) can be accessed on GitHub.

UFO project statistics
----------------------
![Img](/img/L2eYp9A.png)
![Img](/img/24cLZQ8.png)
![Img](/img/Elx28cG.png)


See also
--------

-   [How to install UFO client to generate RSA UFOs](/How_to_install_UFO_client_to_generate_RSA_UFOs "wikilink")
-   [Cryptographic accumulator](/Cryptographic_accumulator "wikilink")
-   [Zerocoin](/Zerocoin "wikilink")

References
----------

Miers, I., C. Garman, M. Green, A. D. Rubin (2013). [| Zerocoin: Anonymous Distributed E-Cash from Bitcoin](http://spar.isi.jhu.edu/~mgreen/ZerocoinOakland.pdf), 2013 IEEE Symposium on Security and Privacy, IEEE Computer Society Conference Publishing Services, pp. 397-411, <doi:10.1109/SP.2013.34>.

Sander, T. (1999). [Efficient Accumulators without Trapdoor Extended Abstract](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.28.4015). In: Information and Communication Security, V. Varadharajan and Y. Mu (editors), Second International Conference, ICICS’99, pages 252-262.

RSA Laboratories. [RSA-768 is factored!](http://www.emc.com/emc-plus/rsa-labs/historical/rsa-768-factored.htm) [First archived by archive.org on 2013-09-21.](https://web.archive.org/web/20130915000000*/http://www.emc.com/emc-plus/rsa-labs/historical/rsa-768-factored.htm)