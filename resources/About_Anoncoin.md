---
title: About Anoncoin
permalink: /About_Anoncoin/
---

[right|200 px](/File:Ip.bitcointalk.png "wikilink") **Anoncoin** (trading symbol ANC) is a digital cryptocurrency that focuses on privacy and anonymity for its users. Created in June 2013, it is the first (and currently only) coin that provides built in support for the [I2P](/I2P "wikilink") darknet that makes it impossible to determine the IP address of the user. Anoncoin also has built in support of [Tor](/Tor "wikilink"), which can help conceal your location and keep your internet traffic private. A long-term goal of Anoncoin is to implement [Zerocoin](/Zerocoin "wikilink"), which will allow users to make transactions that can not be linked in the block chain. With I2P and Zerocoin, Anoncoin will be the first truly anonymous cryptocurrency.

The Anoncoin network is maintained by decentralized miners who process transactions into blocks that are added to the public block chain. With the creation of each block, a specific amount of anoncoin is created that is rewarded to the miner. There can be only about 3.1 million coins created, which is approximately 7 times less than the Bitcoin cryptocurrency. The difficulty of the scrypt proof-of-work algorithm is adjusted to ensure that a block is created about every 3 minutes.

Why was Anoncoin created?
-------------------------

Anoncoin was created not only for the purpose of strong user privacy (which is lacking in Bitcoin and all other cryptocurrencies), but also to provide a cryptocurrency that could support an eventual crackdown from hostile governments and central banks. As opposed to many alternative cryptocurrencies that serve only to enrich financially the developers, Anoncoin was released in an entirely transparent manner and with a fair initial coin distribution. Though there was a small [pre-mine](/Premine "wikilink") of 4200 ANC for technical reasons, these coins were returned to the community by a public faucet, bounties, and give-a-ways. The coin is being actively developed, and full anonymity will be provided by the implementation of [Zerocoin](/Zerocoin "wikilink"), with an expected release date at the end of 2015. The developers have a long history of working on internet privacy issues, as is attested by the recent creation of the non-profit organization [Privacy Solutions](http://privacysolutions.no/) and their work with [I2P](/I2P "wikilink").

But aren't other crytocurrencies anonymous?
-------------------------------------------

Cryptocurrency transactions are stored in a public ledger that allows any outside party to track the history of any payment. By data-mining the block chain, it can be possible in some cases to link a series of public addresses to an individual. By use of other information outside of the block chain, such as digital currency transactions with real-world companies and financial institutions, or the posting of public addresses on web sites, the identity and full transaction history of the user can become compromised.

At the present time (June 2015), there are *no* cryptocurrencies that can honesty claim to be truly anonymous. Several coins or clients offer services that provide increased privacy with respect to the original bitcoin protocol, but *privacy* should not be confused with provable *anonymity*. By default, all other cryptocurrencies perform their transactions on *clearnet*, which makes it possible to [link your IP address to a cryptocurrency public address](https://www.cryptolux.org/index.php/Bitcoin). The existing services for anonymizing the record of a transaction on the public ledger are good only for hiding transactions from unskilled examiners of the blockchain, and often require that you trust their service. As block chain analysis software becomes more common, it will soon be possible for even unskilled examiners to deanonymize certain types of transactions.

The improved privacy services that exist today fall under the general category of coin mixing services. In essence, by mixing the transactions with other users it becomes harder, but not impossible, to link transactions in the block chain. In practice, as the number of people participating in the “mix” increases, the harder it is to figure out after the fact the transaction linkages. Current mixing services include CoinJoin, SharedCoin, CoinShuffle and DarkSend. Crytptocurrencies based on the CryptoNote technology achieve a similar outcome, but by using ring signatures.

The only two protocols that provide 100% provable anonymity are [Zerocoin](/Zerocoin "wikilink") and [Zerocash](/Zerocash "wikilink"). Though different in detail, these two protocols share many similarities in that they make extensive use of [zero-knowledge proofs](/Zero-Knowledge_Proofs "wikilink"). Nevertheless, one major difference is that the setup of Zerocash relies on using trusted third parties. Zerocoin, on the other hand, can be set up in a trustless manner using [RSA UFOs](/RSA-UFO "wikilink") (generalized **RSA** moduli of **u**nknown complete **f**act**o**rization). The RSA-UFOs are generated by each client in a trustless manner from a common public source. To date, we have tested the generated [RSA UFOs](/RSA-UFO "wikilink") to remove small factors and dismiss those that were factorized; the remaining ones will be used to set up Zerocoin in a trustless manner.

Coin details
------------

[right|550 px](/File:ANCminedtime.PNG "wikilink") The defining features of the Anoncoin cryptocurrency are:

-   **Launch date:** June 6, 2013.
-   **Type:** Proof of work with Scrypt hashing algorithm.
-   **Total coin supply:** 3,103,954 ANC.
-   **Block target speed:** 3 minutes (before block 87777, it was every 3.42 minutes)
-   **Block speed retargeting:** every block, using Kimoto Gravity Well (before block 87777, it was ~1680 blocks using classic BTC algorithm)
-   **Current block reward:** 2.5 ANC per block.
-   **[Premine](/Premine "wikilink"):** 1000 blocks (4200 ANC) that were returned to the community by community donations and a public faucet.
-   **Anonymity:** Built in support of I2P and Tor. Zerocoin to be implemented in a future release.

Anoncoin was originally a fork of the Litecoin source code and it now includes most aspects of Bticoin core 0.10. The creation of new coins is by the reward to miners for processing transactions into blocks that are added to the block chain, where mining is performed by proof of work using the [scrypt](/scrypt "wikilink") hashing function. A total of 3.1 million coins can be mined into existence, which is 7 times less than the maximum supply of Bitcoin, and transactions are processed, on average, every 3 minutes. The current block reward is 2.5 ANC, and this will be halved to 1.25 on approximately October 30, 2016.

The block reward distribution schedule is the following: 4.2 ANC for the first 42,000 blocks; 7 ANC for blocks up until 77,777; a 10 ANC bonus block for 77778; 5 ANC until block 306,600; and then halving of block rewards every 306,600 blocks (which is approximately every one year and nine months or 638 days). There were 4200 ANC [premined](/Premine "wikilink") by the developers, but these coins were returned to the community through the faucet and by give-aways.

Since the initial fork, the Anoncoin developers added built in support for the [I2P](/I2P_Anonymous_Network "wikilink") (the Invisible Internet Project) darknet and [Tor](/Tor "wikilink") network. By use of I2P (and to a lessor extent with Tor) it becomes impossible for anyone, including an internet service provider, to determine where the Anoncoin client is being run. Though Anoncoin transactions can still be tracked by the public block chain ledger, the location at which a coin was spent is inherently untrackable. Anoncoin aims to rectify the problem of trackable linkages in the block chain by the possibility of converting anoncoins into [zerocoins](/zerocoin "wikilink"). Once a zerocoin is redeemed for anoncoin to a new public address, it is provably impossible to link this new public address to the address used in minting the original zerocoins. This process is achieved by using [cryptographic accumulators](/cryptographic_accumulator "wikilink") and [commitment schemes](/Commitment_scheme "wikilink") with [zero-knowledge proofs](/Zero-Knowledge_Proofs "wikilink").

See also
--------

-   [Anonymity of cryptocurrencies](/Anonymity_of_cryptocurrencies "wikilink")
-   [How to setup Anoncoin to use Tor](/How_to_setup_Anoncoin_to_use_Tor "wikilink")
-   [I2P](/I2P "wikilink")
-   [Tor](/Tor "wikilink")
-   [Zerocoin](/Zerocoin "wikilink")

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Zerocoin](/Category:Zerocoin "wikilink")