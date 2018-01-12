---
layout: page
title: Roadmap
permalink: /Roadmap/
date:   2018-01-12 10:44:35 +0200
---

Roadmap is updated on Github:
[https://github.com/Anoncoin/project/tree/master/roadmap](https://github.com/Anoncoin/project/tree/master/roadmap)

The roadmap below is old.


---------------------


0.9.7 release - December 2017
---------------------

-   New DNS Seeds.
-   CMake build system (finally trashing autotools).
-   Bugfixes and improvements.
-   Add new alert key?

[Discuss the roadmap on Github](https://github.com/Anoncoin/anoncoin/issues/3)



Last official release
---------------------

-   Anoncoin Core Version 0.9.6.13
-   Release date: 24. June 2017
-   [Github source download](https://github.com/Anoncoin/anoncoin/archive/5e441d8.zip)

-----------------------------------

## History


### Release A

Anoncoin 0.9.6.12 is complete <https://github.com/Anoncoin/anoncoin/releases/tag/v0.9.6.12>

-   Improve i2pd compatibility to match java router → **DONE**

Anoncoin I2Pd ANCI2Pd portable was released for windows <https://github.com/Anoncoin/anoncoin/releases/tag/1.0.12.0>

### Rebuild infrastructure

-   Block explorer

<!-- -->

-   Exchanges

<!-- -->

-   Docker image for build

<!-- -->

-   New bootstrap.dat file

<!-- -->

-   Refresh Anoncoin.i2p for our russian friend at i2pd project

### Release B

-   Implement AUX-POW: Scrypt merge mined with LTC

### Release C

-   Add built-in I2P router, via LibI2Pd (Will now be launched as a subprocess if SAM bridge isn't found at startup. All traffic to be enforced over I2P) → **ONGOING**

<!-- -->

-   Multi-wallet logic

<!-- -->

-   Better support for Qt styling → **ONGOING**

<!-- -->

-   Multi-wallet enabled in Qt → **ONGOING**

<!-- -->

-   Zerocoin



CWalletCoin → **DONE**

zerocoin_wallet storage → **DONE**

RPC mint txn → **DONE**

relaying mint txns → **DONE**

accum. chkpts in block → **PARTIALLY DONE/ONGOING**

wallet witness update

wallet mint logic

refactor CoinSpend

RPC create spend + impl.

store own spend pieces locally

RPC get seeding spend proofs

net: seed spends

net: receive and verify spends

store received spend pieces

wallet spend logic

debugging

GUI → **Ssuag**

debugging

testnet-6