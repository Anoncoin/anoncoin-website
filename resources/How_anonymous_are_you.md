---
layout: page
title: How anonymous are you
permalink: /How_anonymous_are_you/
---

A quick overview of privacy in cryptocurrency transactions.

The blockchain is a public ledger
---------------------------------

When you are sending coins to someone, the transaction is made public in the blockchain.


[600px](/File:Ip.bitcointalk-5.jpg "wikilink")

Cryptocurrency transactions are stored in a public ledger that allows any outside party to track the history of any payment. By data-mining the blockchain, it can be possible in some cases to link a series of public addresses to an individual. By use of other information outside of the blockchain, such as digital currency transactions with real-world companies and financial institutions, or the posting of public addresses on web sites, the identity and full transaction history of the user can become compromised.

How good is coin mixing ?
-------------------------

Several coins or clients claim to offer services that provide increased privacy, but privacy should not be confused with provable anonymity.


[600px](/File:Ip.bitcointalk-1.jpg "wikilink")

The improved privacy services that exist today fall under the general category of coin mixing services. In essence, by mixing the transactions with other users it becomes harder, but not impossible, to link transactions in the blockchain. In practice, as the number of people participating in the “mix” increases, the harder it is to figure out the transaction linkages. Current mixing services include CoinJoin, SharedCoin, and DarkSend. Crytptocurrencies based on the CryptoNote technology achieve a similar outcome, but by using ring signatures.


[600px](/File:Ip.bitcointalk-2.jpg "wikilink")

These existing services for anonymizing the record of a transaction on the public ledger are good only for hiding transactions from unskilled examiners of the blockchain. As blockchain analysis software becomes more common, it will be possible for even unskilled examiners to deanonymize certain types of transactions.

Provable anonymity ?
--------------------


[600px](/File:Ip.bitcointalk-3.jpg "wikilink")

The only two protocols that provide 100% provable anonymity are Zerocoin and Zerocash. Though different in detail, these two protocols share many similarities in that they make extensive use of zero-knowledge proofs.

With Zerocoin, one can create new coins recorded inside the blockchain, but separated from the regular coins. Let's say you have 2 anoncoins whose history you want to erase. By using Zerocoin you would exchange 2 anoncoins for 2 zerocoins, which would be added to all the other zerocoins in a cryptographic accumulator, waiting to be redeemed. At that point they become totally unrelated to any Anoncoin addresses.


[<File:Ip.bitcointalk-4.jpg>](/File:Ip.bitcointalk-4.jpg "wikilink")

When you want to get some anoncoins back, all you have to do is to prove that you previously created 2 zerocoins, in order to receive someone else's 2 anoncoins coming from that zerocoin pool and without their previous history.

Regarding Zerocoin and Zerocash, one major difference is that the setup of Zerocash relies on using trusted third parties. Zerocoin, on the other hand, can be set up in a trustless manner using RSA UFOs.

**Currently, the Anoncoin developers have finished testing the RSA UFOs that will be used to set up Zerocoin in a trustless manner. Zerocoin integration will be worked up after 2016 hardfork.**

[Category:Press](/Category:Press "wikilink") [Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Zerocoin](/Category:Zerocoin "wikilink")