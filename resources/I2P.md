---
layout: page
title: I2P
permalink: /I2P/
---

<div class='pull-right' markdown="1">
![Image](/img/imgres.jpg)
</div>

 **I2P** (an acronym for the Invisible Internet Project) is an anonymous overlay network - a network within a network. It is intended to protect communication from dragnet surveillance and monitoring by third parties such as ISPs. I2P is used by many people who care about their privacy: activists, oppressed people, journalists and whistleblowers, as well as the average person. No network can be “perfectly anonymous”. The continued goal of I2P is to make attacks more and more difficult to mount. Its anonymity will get stronger as the size of the network increases and with ongoing academic review.

How does it work?
-----------------

I2P is an anonymous network, exposing a simple layer that applications can use to anonymously and securely send messages to each other. The network itself is strictly message based (à la IP), but there is a library available to allow reliable streaming communication on top of it (à la TCP). All communication is end to end encrypted (in total there are four layers of encryption used when sending a message), and even the end points (“destinations”) are cryptographic identifiers (essentially a pair of public keys).

To anonymize the messages sent, each client application has their I2P “router” build a few inbound and outbound “tunnels” - a sequence of peers that pass messages in one direction (to and from the client, respectively). In turn, when a client wants to send a message to another client, the client passes that message out one of their outbound tunnels targeting one of the other client's inbound tunnels, eventually reaching the destination. Every participant in the network chooses the length of these tunnels, and in doing so, makes a tradeoff between anonymity, latency, and throughput according to their own needs. The result is that the number of peers relaying each end to end message is the absolute minimum necessary to meet both the sender's and the receiver's threat model.

The first time a client wants to contact another client, they make a query against the fully distributed “network database” - a custom structured distributed hash table (DHT) based off the Kademlia algorithm. This is done to find the other client's inbound tunnels efficiently, but subsequent messages between them usually includes that data so no further network database lookups are required.

What can you do with it?
------------------------

Within the I2P network, applications are not restricted in how they can communicate - those that typically use UDP can make use of the base I2P functionality, and those that typically use TCP can use the TCP-like streaming library. There is a generic TCP/I2P bridge application (“I2PTunnel”) that enables people to forward TCP streams into the I2P network as well as to receive streams out of the network and forward them towards a specific TCP/IP address.

I2PTunnel is currently used to let people run their own anonymous website (“eepsite”) by running a normal webserver and pointing an I2PTunnel 'server' at it, which people can access anonymously over I2P with a normal web browser by running an I2PTunnel HTTP proxy (“eepproxy”). In addition, the same technique is used to run an anonymous IRC network (where the IRC server is hosted anonymously, and standard IRC clients use an I2PTunnel to contact it). There are other application development efforts going on as well, such as one to build an optimized swarming file transfer application (à la BitTorrent), a distributed data store (à la Freenet/MNet), and a blogging system (a fully distributed LiveJournal), but those are not ready for use yet.

I2P is not inherently an “outproxy” network - the client you send a message to is the cryptographic identifier, not some IP address, so the message must be addressed to someone running I2P. However, it is possible for that client to be an outproxy, allowing you to anonymously make use of their Internet connection. To demonstrate this, the “eepproxy” will accept normal non-I2P URLs (e.g. “<http://www.i2p.net>”) and forward them to a specific destination that runs a squid HTTP proxy, allowing simple anonymous browsing of the normal web. Simple outproxies like that are not viable in the long run for several reasons (including the cost of running one as well as the anonymity and security issues they introduce), but in certain circumstances the technique could be appropriate.

The I2P development team is an open group, welcome to all who are interested in getting involved, and all of the code is open source. The core I2P SDK and the current router implementation is done in Java (currently working with both sun and kaffe, gcj support planned for later), and there is a simple socket based API for accessing the network from other languages (with a C library available, and both Python and Perl in development). The network is actively being developed and has not yet reached the 1.0 release, but the current roadmap describes our schedule.

Where to download I2P
---------------------

The official I2P release can be downloaded here: <https://geti2p.net/en/download>.

Differences between I2P and Tor
-------------------------------

-   <http://null-byte.wonderhowto.com/how-to/tor-vs-i2p-great-onion-debate-0133642/>
-   <https://geti2p.net/en/comparison/tor>

See also
--------

-   [Tor](/Tor "wikilink")
-   [How to install and use I2P](/How_to_install_and_use_I2P "wikilink")
