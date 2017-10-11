---
layout: page
title: Development schedule
permalink: /Development_schedule/
---

Last official release
---------------------

-   Anoncoin Core Version 0.9.6.12
-   Release date: 12 Oct 2016
-   [Github source download](https://github.com/Anoncoin/anoncoin/tree/master)

------------------------------------------------------------------------

-   ANCI2Pd Portable (win32) <https://github.com/Anoncoin/anoncoin/releases/tag/1.0.12.0>

Tentative Anoncoin release schedule
-----------------------------------

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

-   **Hard fork required**

To-do list
----------

*Looking for volunteers to help...*

-   Open new ANC forum (at forum.anoncoin.net?)
-   Add language-translation functionality to the wiki (current implementation is not good).
-   Mirror the wiki to I2P
-   Make a guide on how to clone the I2P git repo (to direct git to go over I2P tunnel to build Anoncoin).
-   Finish the translations on Transifex
-   Port a block explorer on I2P (ABE)?
-   Implement [Hierarchical Deterministic Wallets](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)
-   Port [PyWallet](https://github.com/jackjack-jj/pywallet) to Anoncoin?
-   Add multisig support to the Qt client.