---
layout: page
title: How to rebroadcast transaction
permalink: /How_to_rebroadcast_transaction/
---

Sometimes exchanges have problem with broadcasting efficiently a transaction. As long as a transaction is not confirmed it is essentially **NOT VALID** hence **they still owe the user the Anoncoins**. For them to not rebroadcast a transaction is considered a theft, sadly many do not want to give RAW transaction ID to the user, for unknown reason because it is **NOT** a risk for them. **This show only their incompetentence, or they are trying to steal their user by faking transaction that will never be broadcasted.**

This guide is made for the user to show if exchanges using these shady techniques are honest or not, and for the exchange to help their user to solve the issues.

The user shall provide it to them whenever the exchanges do not want to rebroadcast a transaction or provide a TXID. Sometimes these exchanges (**Cryptsy**, **BTC38**) use pictures to show the transaction was done by them but **the user shall never forget that if a transaction is not taken up by the blockchain and is not confirmed it is not valid**.

![Image](/img/1458972596x3738746559.png)

Such a picture only show that the exchange did a transaction but going into an explorer <https://coinplorer.com/ANC/Transactions/69c9369368c9dc2dbca8361c3297c2089dd26e99b07dac40bd1bb7eabd41cf67> we see it was not accepted by the blockchain:

![Image](/img/Capture_3.PNG)

To know if the exchange is honest (**Cryptsy is definitely NOT honest**!) or if the exchange is faking withdrawal error to steal your anoncoin, the user shall ask the helpdesk to do the following. If the exchange is honest, they shall do like shown below to help the user.

For the exchanges, to rebroadcast a transaction
-----------------------------------------------

Easiest way: using the newly enabled on 0.9.6.11 “`resendwallettransactions`” command. Exchange can type it (in the debug console or with anoncoin-cli) when they are well connected and if they did not close their wallet since the failed transaction attempt.

```
23:56:37 help resendwallettransactions

23:56:37 resendwallettransactions

Immediately re-broadcast unconfirmed wallet transactions to all peers.
Note: the wallet code periodically re-broadcasts automatically.
Returns: array of transaction ids that were re-broadcast.
```

Another way via the RAW TX
--------------------------

This is possible when the transaction is not in a block, but the wallet was not closed (**if it is closed the transaction ID TXID is erased**). The process is safe and very simple. In the debug console type `getrawtransaction TXID` (I repeat: this will not work if the wallet was closed since the unconfirmed transaction):

```
07:30:38 getrawtransaction 0235a6c2d98434c3fc72f0ea08781a9263df68cd871f94417ff719fdbe5d5516

07:30:38 01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff0d03ccbd070112062f503253482fffffffff0180b2e60e000000002321032ff1d59f4d061d383ee4cfcaf8cd3fd3d3c573a2f2af9d56e1ee2b2d24c9b1a9ac00000000
```

The response is the RAW TX, it is what should be broadcasted again. If the exchange do not want to give it to the user to rebroadcast the TX, the exchange has to type sendrawtransaction RAW TX in console to rebroadcast a RAW TX:

```
10:12:14 sendrawtransaction 01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff0d03ccbd070112062f503253482fffffffff0180b2e60e000000002321032ff1d59f4d061d383ee4cfcaf8cd3fd3d3c573a2f2af9d56e1ee2b2d24c9b1a9ac00000000

10:12:14 transaction already in block chain (code -27)
```



If it is already in block chain the error code -27 above will be answered, otherwise the transaction will be rebroadcasted to connected peer.

**IF THE EXCHANGE DO NOT WANT TO DO THIS EASY PROCESS, PLEASE COMPLAIN FOR STEALING OF ANONCOIN IN BITCOINTALK THREAD [1](https://bitcointalk.org/index.php?topic=227287.5000)!**