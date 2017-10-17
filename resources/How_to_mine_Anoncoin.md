---
layout: page
title: How to mine Anoncoin
permalink: /How_to_mine_Anoncoin/
---

You can mine [Anoncoin](/About_Anoncoin) on your computer by using [scrypt](/scrypt) ASICs. It is no longer profitable to mine with either a GPU or CPU.

Mining at a P2Pool pool
-----------------------

Instructions on how to mine at a P2Pool can be found here: [<https://bitcointalk.org/index.php?topic=153232.0>](https://bitcointalk.org/index.php?topic=153232.0) and [<https://bitcointalk.org/index.php?topic=457574.0>](https://bitcointalk.org/index.php?topic=457574.0)

If you would like to set up your own pool, here is the code! [<https://github.com/K1773R/p2pool>](https://github.com/K1773R/p2pool)

Mining with Scrypt ASICS
------------------------

Change your anoncoin.conf file to include the following:

```
stfu=1
rpcallowip=192.168.1.*
rpcport=9376
rpcuser=******yourusername******
rpcpassword=******yoursecretpassphrase******
server=1
daemon=1
gen=0
listen=1
```

`rpcuser` and `rpcpassword` can be anything of your choosing, and `rpcallowip` is the IP address of your ASIC. Open your wallet on the computer (either with `anoncoind` or `anoncoin-qt`), and point the ASIC to that computer IP address and port 9376 using your rpc username and password.

See also
--------

-   [Mining pools](/Mining_pools)
