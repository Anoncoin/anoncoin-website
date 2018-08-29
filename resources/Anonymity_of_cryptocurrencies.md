---
layout: page
title: Anonymity of cryptocurrencies
permalink: /Anonymity_of_cryptocurrencies/
---

How anonymous are you?
----------------------

In digital networks, anonymity is the lack of evidence that can reveal the true identity, social details and location of someone. Whereas the absence of identity details, such as names or adresses, is the first step to achieve anonymity, it is not sufficient in the context of digital block chain based transactions using Bitcoin and other cryptocurrencies. This partial anonymity is pseudonymous rather than anonymous: All of your transactions are visible, and the only thing that protects you is a “fake” name.

### The block chain is a public ledger

![Ledger](/img/Ip.bitcointalk-5.jpg)

Bitcoin transactions are all stored, by design, in a public ledger (the block chain) that is accessible to everyone. These transactions provide privacy through pseudonymity, in that while each transaction is associated with the public address of the sender and receiver, the real-life names of the owners of these addresses are at no time made known to the network. To increase privacy, each person could create as many public addresses as they like, making it difficult to link transactions to the same person.

### Linking addresses to social details

Regardless of the best precautions, it is possible in certain cases to link a set of public addresses to a specific individual. For example, by data mining the block chain or by the analysis of spending habits, it is possible to link sets of addresses. By utilizing information external to the block chain, such as public addresses posted on a web site or the postal address used with an internet purchase, the possibility exists that every single transaction of a given person could be determined. If all your transactions could be deanonymized, this would be analogous to publishing the full contents of your bank account on line for all to see.

### IP address

When making a cryptocurrency transactions, the data are sent from the users computer, revealing the IP address. This IP address is seen by the nodes of the cryptocurrency network used, or anyone else who is snooping on your traffic. IP addresses are not stored in the block chain, but a motivated attacker could gather this information. If successful, this would be a serious threat to one's anonymity.

### Censorship

Note that Internet Service Providers and any other entity capable of monitoring the network can see the nature of the transactions going through it. Bitcoin-like cryptocurrencies, while using asymmetric encryption, do not encrypt transactions: They are only cryptographically signed. Setting up a proxy can be useful, but in such circumstances one should also ensure to create an encrypted tunnel to bypass monitoring. See Tor and I2P below.

### Proxies

It is possible to hide your home IP address by using some kind of proxy. Simple proxies will only hide it, while the use of more complex routing networks such as Tor or [I2P](/I2P/) will also encrypt the connexion between your computer and the nodes that can see your IP. Anoncoin can be set up to use Tor using [these instructions](/How_to_setup_Anoncoin_to_use_Tor/).

I2P is another routing network that hides your IP address, and for now, Anoncoin is the only cryptocurrency that is configured to use it. I2P is not an outbound proxy like Tor. Anoncoin can be easily configured to use I2P by following these [these instructions](/How_to_setup_your_Anoncoin_wallet/).

For an explanation of the differences between Tor and I2P, see this link: <https://geti2p.net/en/comparison/tor>

### Mixing

![Mixing](/img/Ip.bitcointalk-1.jpg)

It is possible to launder coins through a trusted third party, where the input coins are mixed in a large pool and output to a new address [1](http://www.coindesk.com/how-anonymous-is-bitcoin/). This is not a strong anonymity method given that you need to trust the service where you send the coins. A similar possibility would be to use an exchange where you could convert one cryptocurrency into another one. By doing so, you would get some coins from which the original source is very difficult to guess, but not impossible either. You would need to trust the exchanges, and it is possible that the exchange could provide their logs if asked by law enforcement.

### Conclusion

In conclusion, the public nature of the block chain is, paradoxically, a great tool and a big concern, because there are now special offices that provide block chain investigation services. That's why there must exist a strong way of anonymizing transactions when needed.

![Conclusion](/img/Ip.bitcointalk-2.jpg)

Privacy-centric cryptocurrencies: methods and issues
====================================================

Many coins or services now claim to have special features that provide “anonymity”, and it can be hard to find what is really cryptographically strong and what is not. In most cases, these services provide only increased privacy, by making it really hard (but not impossible) to trace the origin of a given transactions. Only two methods Zerocoin Zerocash provide cryptographically proven anonymity. Below, we provide a review of these services.

Embedded tools or online services
---------------------------------

### Stealth addresses

-   Stealth addresses are equivalent to using single use public addresses. With a stealth address, you ask a payer to generate a unique address in such a way that you (using some additional data which is attached to the transaction) can deduce the corresponding private key. Even though you publish a single “stealth address” on your website, the block chain sees all your incoming payments as going to separate addresses and has no way to correlate them.

<!-- -->

-   Should work with any block-chain based cryptocurrency.

### Dark Wallet

-   Dark wallet is not a real coin, just is rather just a client that is intended to be used with bitcoin.

<!-- -->

-   Mixes transactions in a centralized server.

<!-- -->

### CoinJoin (and derivatives, such as Sharedcoin used in blockchain.info)

-   This is simply a decentralized mixing pool the joins multiple transaction inputs in a single block and mixes them into different outputs in the same block.

<!-- -->

-   Anonymity is limited to the number of coins that participated in the mix for the given blocl. If implemented correctly, the algorithm does not require trust: [3](http://crypsys.mmci.uni-saarland.de/projects/CoinShuffle/coinshuffle.pdf)

<!-- -->

-   Vulnerable to syble attack and sophisticated block chain analysis.

<!-- -->

-   Transaction size increases with anonymity set (number of people mixing)

<!-- -->

-   Coinjoin white paper here : [4](http://www0.cs.ucl.ac.uk/staff/G.Danezis/papers/DanezisFournetKohlweissParno13.pdf)

Specific cryptocurrencies with simple approach
----------------------------------------------

### So called Torcoins (Stealthcoin, SSD, etc.)

-   Only hides the IP addresses to the nodes when using Tor.

<!-- -->

-   The block chain is still public, and so are the transactions. The achieved anonymity is the same as using Bitcoin with Tor.

### Cloakcoin

-   No cryptographic litterature or code base to review.

<!-- -->

-   Several possible flaws with proposed POSA have been unanswered.

### Mixing Coins (Fedoracoin, NEM, XCurrency)

-   Transactions are mixed on centralized servers, so that they are harder to link, but the block chain is still public.

<!-- -->

-   Hosted services are centralized and require that you trust these entities. If the server is compromised, any log or monitoring can reveal the origins of transactions.

<!-- -->

-   *Xcurrency* uses Coinjoin mixing with a proprietary tool (not open source so cannot be publicly audited) called “Coinshuffle” and says it mixes coins in a trustless manner.

### BitcoinDark

-   Teleport feature (review, code source or white paper ?)

<!-- -->

-   See discussion here: [6](https://bitcointalk.org/index.php?topic=684090.0/)

### Darksend of Darkcoin (Cousin coins : X11, BlackCoin)

-   Dark send is a feature of the Darkcoin wallet that is based on CoinJoin. It uses limited number of “MasterNodes” to mix coins.

<!-- -->

-   One has to get 1000 DarkCoins and stake them in order to set up a MasterNode. The developpers' philosophy is to set a high cost to run Masternodes, so they're more difficult to compromise.

<!-- -->

-   The coin had several fork issues in its short history, and MasterNodes could have been be compromised at least once. See here: [7](http://thecoinfront.com/darkcoin-price-crashes-after-massive-blockchain-fork/)

<!-- -->

-   The code has just been open sourced, many months after its launch.

<!-- -->

-   White paper : [10](http://www.darkcoin.io/downloads/DarkcoinWhitepaper.pdf)

More complex cryptographic approaches
-------------------------------------

### CryptoNote & derivatives (Bytecoin, Monero, etc.)

-   Uses *Ring Signatures* : many users (including the sender) sign a transaction to make it very difficult to find the true sender amongst all the signers.

<!-- -->

-   Anonymity limited to number of keys on the ring. The more keys there are, the more your privacy is assured. However, using more keys requires a higher computational cost.

<!-- -->

-   Transaction size increases with the number of people participating in the ring signature. Block chain bloat occurs when there are a large number of signers.

<!-- -->

-   Block chain transactions and payments are not public anymore, but total amount of coins in the network can still be viewed.

<!-- -->

-   Cryptonote white paper: [11](https://cryptonote.org/whitepaper.pdf)

### Zerocoin, using RSA UFOs

-   Zerocoin was originally developed by a team of academic cryptographers who wanted to add true cryptographic anonymity to Bitcoin. In part because the Bitcoin community was not interested in incorporating zerocoin capabilities, these academics moved on to a different project, called called Zerocash. [12](http://zerocoin.org/people)

<!-- -->

-   Zerocoin is now being developped by [Anoncoin](/About_Anoncoin/). Though many other coins claim to be implementing Zerocoin as well, none besides Anoncoin have given proof of such activity.

<!-- -->

-   In Zerocoin, the user convertd the traditional base currency to and from zerocoins, which are a second currency that shares the same block chain. Zerocoin acts like a money laundering pool, temporarily pooling coins together at the protocol level.

<!-- -->

-   By analyzing the block chain, you can see when someone buys zerocoins, and you can also see when zerocoins are redeemed to a public address. However, by the use of [Zero-knowledge proofs](/Zero-knowledge_proof/), it is not possible to link the original address that bought the zerocoins to the address where they are eventually redeemed.

<!-- -->

-   In order to set up zerocoin, several security parameters need to be chosen which are simply products of two large prime numbers. Anoncoin uses [RSA UFOs](/RSA_UFO/) for these numbers, whose factorization is unknown, even to the person who generated the number. The use of RSA UFOs makes Anoncoin's implementation of Zerocoin entirely trustless.

<!-- -->

-   Transactions sizes are not increased substantially in the blockchain, because most information is stored in a secondary database that is periodically deleted.

![Mixing](/img/Ip.bitcointalk-4.jpg)

### Zerocash

-   Zerocash was developed by some of the same authors as Zerocoin. This will be a coin of its own, but it has not yet been released.

<!-- -->

-   In contrast to Zerocoin, Zerocash hides the amounts of the transaction inputs and outputs. As a result of this, it is not possible to monitor the total money supply.

<!-- -->

-   Uses Succinct Non-Interactive Zero-Knowledge Proofs (zk-SNARK) which requires trusted third parties when setting up the initial security parameters. If these parameters were uncovered, a malicious agent could forge an unlimited number of completely undetectable transactions.

A word on trust
---------------

In the fields of networks and cryptography, when a service has to know and store data that can be used to defeat the process of anonymity, trust is about the ability to protect this content and not be using it for other purposes.

Any anonymity process requiring that you “trust” such a service is weak compared to the security provided by fully trustless cryptographic system (such as Zerocoin and Zerocash).

See also
--------

-   [How anonymous are you](/How_anonymous_are_you/)
