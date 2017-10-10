---
layout: page
title: How to run a DNS seeder
permalink: /How_to_run_a_DNS_seeder/
---

**DNSSeed Guide**
09.11.2014 // K1773R &lt;k1773r@darkgamex.ch&gt;

### Prerequisites

-   IPv4 with UDP/53 open/available
-   Domain name (does not have to be a top-level domain)
-   The following packages installed on your system:



git, screen, gcc, g++, libcrypto++-dev, make, bash, libboost?-dev, libssl-dev

(*substitute ? with a version of your choice*)

-   Magic-Bytes of your coind (pchMessageStart)
-   Running \*coind

### Compiling

`$ mkdir -p ~/git`
`$ git clone `[`https://github.com/K1773R/bitcoin-seeder.git`](https://github.com/K1773R/bitcoin-seeder.git)` ~/git/bitcoin-seeder`
`$ cd ~/git/bitcoin-seeder`
`$ make -j'nproc'`

### Configuration

`$ mkdir -p ${HOME}/.dnsseed-anoncoin`

-   For the DNS setup, see the section USAGE in the file ~/git/bitcoin-seeder/README
-   Use an example startscript of the following form (http://pastebin.com/VCvT7Mpc):

`#!/bin/bash`
`SEED=127.0.0.1`
`HOST=anc.dnsseed01.anoncoin.darkgamex.ch`
`NAMESERVER=dnsseed01.anoncoin.darkgamex.ch`
`P2PORT=9377`
`MAGIC=FACABADA`
`SOA=K1773R.darkgamex.ch`
`TOR=127.0.0.1:9050`
`CRAWLER_THREADS=250`
`DNSSERVER_THREADS=50`
` cd ${HOME}/.dnsseed-anoncoin`
`screen -S dnsseed-anoncoin ~/git/bitcoin-seeder/dnsseed -h ${HOST} -n ${NAMESERVER} \`
`--p2port ${P2PORT} --magic ${MAGIC} --seed ${SEED} -m ${SOA} -o ${TOR} \`
`-t ${CRAWLER_THREADS} -d ${DNSSERVER_THREADS}`

-   then adjust the following required settings:

`HOST=`<YOUR HOST>
`NAMESERVER=`<YOUR HOSTNAME FOR NAMESERVER>
`P2POPRT=<*coind p2poort>`
`MAGIC=`<Magic-Bytes>
`SOA=`<Contact E-Mail, no @ allowed>

-   and set the following optional settings

`TOR=`<IP:port>
`CRAWLER_THREADS=`<Amount of crawler threads>
`DNSSERVER_THREADS=`<Amount of DNSserver threads>

### Running

Just execute the startscript that you set up in the preceding section.

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")