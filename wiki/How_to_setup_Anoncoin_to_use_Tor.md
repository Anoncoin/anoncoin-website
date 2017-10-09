---
title: How to setup Anoncoin to use Tor
permalink: /How_to_setup_Anoncoin_to_use_Tor/
---

Running Anoncoin behind a [Tor](/Tor "wikilink") proxy will attempt to anonymize all incoming and outgoing traffic, and also allow you to connect to Tor hidden services. The following directions assume you have a Tor proxy running on port 9050. Many distributions default to having a SOCKS proxy listening on port 9050, but others may not. In particular, the [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en) defaults to listening on port 9150. See [this link](https://www.torproject.org/docs/faq.html.en#TBBSocksPort) for how to properly configure Tor.

First, a warning
----------------

Although Tor can help conceal your location and keep your internet traffic private, you can be deanonymized if an attacker controls both your entry and exit points to and from the Tor network. Hidden services [have](https://blog.torproject.org/blog/thoughts-and-concerns-about-operation-onymous) been deanonymized by national security agencies, and these attacks will become more sophisticated as Tor research continues. Anoncoin was built to take advantage of the superior I2P anonymizing network. We can only advocate using Tor with Anoncoin if privacy is absolutely required, and if it is not possible to access the I2P network.

Running the Anoncoin-Qt client behind a Tor proxy
-------------------------------------------------

To set up the Qt client to work with Tor, follow these easy steps.

1.  Setup and run Tor on your computer.
2.  Open the Anoncoin=Qt client.
3.  In the Anoncoin client preferences, go to “Network.”
4.  Click on “Connect through SOCKS proxy.”
5.  Set the proxy IP to “127.0.0.1”, the port to “9050”, and the SOCKS version to “5.”
6.  Click “ok”, and restart the Anoncoin client.

That's it!

Running the Anoncoin daemon (anoncoind) behind a Tor proxy
----------------------------------------------------------

The Anoncoin daemon (run at the command line) accepts the following Tor-related options:

`-proxy=ip:port`


Set the proxy server for IPv4/v6 traffic. By default, this proxy server will be used to try to reach .onion addresses as well.

`-onion=ip:port`


Set the proxy server that is use only for connecting to Tor hidden services. You do not need to set this if it's the same as `-proxy`. If you do not want to use a proxy server for your IPv4/v6 traffic, but do want to reach onion addresses, do not specify `-proxy`.

`-connect=xxxx.onion`, `-addnode=xxxx.onion`, `-seednode=xxxx.onion`


When behind a Tor proxy, you can specify .onion addresses instead of IP addresses or hostnames in these parameters.

In a typical situation, it suffices to use this command to run `anoncoind` behind a Tor proxy:

`anoncoind -proxy=127.0.0.1:9050`

If you want to connect only to Tor hidden services, and not to nodes that are reachable by IPv4/v6 (via Tor), then use

`anoncoind -onion=127.0.0.1:9050 -onlynet=tor`

If desired, the command line options can be set directly in the `anoncoin.conf` file using the syntax

`proxy=127.0.0.1:9050`
`onion=127.0.0.1:9050`
`onlynet=tor`
`connect=xxxx.onion`
`addnode=xxxx.onion`
`seednode=xxxx.onion`

Note that it is possible to set both `onlynet=tor` and `onlynet=i2p`, so that all traffic is sent through either I2P or Tor hidden servers.

How to run an Anoncoin Tor hidden service
-----------------------------------------

If you have set up Anoncoin to run behind a Tor proxy, it is simple to make your node reachable from the Tor network by creating a hidden service. First, add these lines to your `torrc` configuration file (found in /etc/tor/, or /usr/local/etc/tor/)

`HiddenServiceDir /var/lib/tor/anoncoin-service/`
`HiddenServicePort 9377 127.0.0.1:9377`

The hidden service directory can be different than above: On OSX use “`~/Library/Application`` ``Support/Tor/anoncoin-service`”. After restarting Tor, the hidden service directory should contain two new files, with the file `hostname` containing your .onion address. When starting `anoncoind`, the following parameters, in addition to those of the previous section, can then be set:

`-externalip=xxxx.onion`


Use this option to specify your publicly reachable .onion address.

`-listen`


When using `-proxy`, listening for incoming connections is disabled by default.

`-discover`


When `-externalip` is specified, no attempt is made to discover local IPv4 or IPv6 addresses. If you want to be reachable from both Tor and IPv4/v6, you'll need to either pass your other addresses using `-externalip`, or explicitly enable `-discover`. Note that your onion and IPv4/v6 addresses may be easily linkable using traffic analysis.

In a typical situation, where you are only reachable via Tor onion addresses, it should only be necessary to start anoncoind with the following options:

`anoncoind -onion=127.0.0.1:9050 -externalip=xxxx.onion -listen -onlynet=tor`

The above command line options are most easily set in the file `anoncoin.conf`, as opposed to specifying them each time `anoncoind` is run:

`externalip=xxxx.onion`
`listen=1`
`discover=0`
`onlynet=tor`

If you don't care too much about hiding your node, and want to be reachable on IPv4/v6 as well, specify:

`anoncoind -onion=127.0.0.1:9050 -externalip=xxxx.onion -listen -discover`

This last option is the best for supporting the Anoncoin network.

Connecting to a Tor hidden server
---------------------------------

The anoncoin client will generally find Tor hidden services to connect to. If you would like to connect to a specific Tor hidden service, this can be done using one of three methods. First, if `anoncoind` is already running, the following command can be issued in the terminal:

`anoncoin-cli addnode xxxx.onion add`

Alternatively, the node can be added directly to the `anoncoin.conf` file using the syntax (one for each node):

`addnode xxxx.onion add`

Lastly, `anoncoind` can be started with the option

`anoncoind -addnode=xxxx.onion`

Known Tor hidden servers
------------------------

-   anoncoinmpkoerba.onion
-   kjwhbac5hwwdimq7.onion
-   isdze75oiisc6kvj.onion

See also
--------

-   [How to setup your Anoncoin wallet](/How_to_setup_your_Anoncoin_wallet "wikilink")
-   [Tor](/Tor "wikilink")
-   [I2P](/I2P "wikilink")

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")