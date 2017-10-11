---
layout: page
title: How to setup your Anoncoin wallet
permalink: /How_to_setup_your_Anoncoin_wallet/
---

Downloading the Anoncoin client and setting up your personal wallet for the first time is simple. Just follow the steps below and you will be up and running in no-time.

Download the Anoncoin client
----------------------------

Choose one of the the following options below.

### MS Windows

You can choose execute the setup.exe from the [extractable zip file](https://anoncoin.net/downloads/0.9.6.11/) to be run from the directory, or just run the included [anoncoind daemon](https://anoncoin.net/downloads/0.9.6.11/) if you won't be using the QT graphic user interface.

### Mac OS X

This only comes in one flavor. The \[ disk volume (dmg) file\] contains all the files needed to run Anoncoin in a single package.

### Linux

Clone the master from [the git repository](https://github.com/Anoncoin/anoncoin), it contains all the source files needed to compile your own binaries. How to guide is here [How_to_build_Anoncoin_from_source](/How_to_build_Anoncoin_from_source "wikilink"). Binaries are in the works for multiple Linux distributions.

### Source Code

Obtain the Anoncoin source code by [cloning the git repository](https://github.com/Anoncoin/anoncoin).

Setting up your client to use I2P (9.6.13)
------------------------------------------

Build the Anoncoin master 9.6.13 from source ([How to build Anoncoin](/How_to_build_Anoncoin "wikilink")).

Alternatively, you can download the master version (19/06/2017) here: <https://github.com/Anoncoin/anoncoin/releases/tag/5e441d8>

If there was a previous installation of Anoncoin 8.5.6, delete everything in anoncoin data directory **BUT KEEP WALLET.DAT** (the data directory is exemplified in the next link about bootstrap).

Download and install java [I2P](/I2P "wikilink") following [How_to_install_and_use_I2P](/How_to_install_and_use_I2P "wikilink")

Install Anoncoin following this guide [How to install Anoncoin](/How_to_install_Anoncoin "wikilink").

Then download and copy the file `bootstrap.dat` in the anoncoin data directory ([How to use a bootstrap file to speed up initial synchronization](/How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization "wikilink")).

Then copy/paste the sample `anoncoin.conf` for the 9.6.12 version in your data directory. It is found in the folder anoncoin/doc or here [Anoncoin-0.9.6.12.conf](/Anoncoin-0.9.6.12.conf "wikilink").

and go at <http://127.0.0.1:7657/configclients>, activate SAM application bridge and make it run at startup, save the configuration.

![Image](/img/Configi2p.PNG)

Then after 5 min, allowing time for the SAM application bridge to launch, start Anoncoin-qtc 9.6.12 with the following command (or run the “Generate I2P static privatekey” shortcut on windows):

`anoncoin-qtc -i2p.options.enabled=1 -onlynet=i2p -generatei2pdestination`

To run in I2P only mode, without anoncoin.conf file, execute (or run the “Anoncoin Core I2P-only” shortcut on windows):

`anoncoin-qtc -i2p.options.enabled=1 -onlynet=i2p`

The I2P address generated above will be used unless another one is specified in anoncoin.conf.

You can also alternativelly go in the menu `settings-options-I2P-generate_I2P_address` and copy this key to anoncoin.conf.

![Image](/img/I2pdetail.png)

Click on `copy `“`mydestination`”` parameter to the clipboard`, edit the `anoncoin.conf` in your data dir and paste the string in the `anoncoin.conf` at the following location:

`privatekey=`

Be sure to remove the \# of this line too.

Do the same with public address and B32 address. Then change in `i2p.options` to `static=1`

It shall look like this:

`[i2p.mydestination]      #do not comment the line with []`
`privatekey=OqCg43bXytCJv*****AAAA****long****`
` `
`[i2p.options]`
`enabled=1`
`static=1                 #Change it to 1 to use [i2p.mydestination] addresses after they are generated and copied above `
`samhost=127.0.0.1      #Change it to i2pd or java i2p host local IP (127.0.0.1 or 192.168.1.5 for instance) `
`samport=7656`

Let the wallet finish to synch (it takes two or three hours normally) then close it and restart, now you are running an I2P-only anoncoin wallet with a static address! :)

Using the command line to generate a random anoncoin address and run anoncoind with I2P
---------------------------------------------------------------------------------------

Install I2P from the PPA repository [1](https://geti2p.net/en/download/debian#ubuntu) and run the i2p router.

`i2prouter start`

Wait 5 minutes for initialisation of the I2P SAM bridge and in anoncoin/src type:

`./anoncoind -i2p.options.enabled=1 -onlynet=i2p -generatei2pdestination`

All the data that are needed to setup the `.anoncoin/anoncoin.conf` will be printed as a result:

`user@ubuntu:~/anoncoin/src$ ./anoncoind -i2p.options.enabled=1 -onlynet=i2p -generatei2pdestination`
`Anoncoin server starting`
`user@ubuntu:~/anoncoin/src$ Generated I2P Destination: `
`To have a permanent I2P Destination address, you have to set options in anoncoin.conf:`
`Your Config file is: /home/yo/.anoncoin/anoncoin.conf`
`Your I2P Destination Private Key anoncoin.conf file settings are:`
`[i2p.mydestination]`
`static=1`
`privatekey=apuLsXH2KdmTV******AAAA****long****`
`[i2p.options]`
`enabled=1`
`****** Save the above text at the end of your configuration file and keep it secret.`
`      Or start with our anoncoin.conf.sample file, which has even more settings.`
`This is your I2P Public Key:`
`apuLsXH2KdmTVUgY-PIJcRyVEOExQCmX4-1olVrOg1g5adVW~DQX9wfwXEMVZTPQn9FqyaU2vrvgXsJuQEECRWGewf4DIylJG9dn-ac6N9LniTbWmbSNyWDOv54qc4yO3LeHyp3Gm2UvaSpdmjXQ0PnLirWXo-HxmvTpD~UunIraX4SRZcijNzBG6jYAdjp8-sTq17kjb9S3Ar33UmJR0G9ir4UrY93zKvUojiylLpNrJKeBkp4YB2RurXkwy6zHt2mavhae7~sKa0YfXcn-ZnUIVbIp~KC~dxhEO~L6VBsbtfki-4M1xRn39~ygI0Y-Ca2nSDgRsEZ9bi8uUbBQgYzSZfsDzAgUNWcQHYZHHX39cP-S8Du~yU4Ioy3cC~pa31Inv3RcfR9ZX1qxrBsPiDEdgtfvbO1ahNxgeTVnhYg-6n--jxqLDEI1rOpzFJD0yHfNKcjeJ5nKq5cwFBRjeAlBKGNmHioILIOcz48Woq1OQdnfthA6zDGEfnwmN~eYAAAA`
`**** You can advertise the Public Key, all I2P Routers will know how to locate it.`
`Your personal b32.i2p Destination:`
`5oo3enrz7fp77ojrfk7hjsniohsxqmhuxdhdx6ur7iwumsrjzkwq.b32.i2p`
`** Anoncoin peers now have built-in name resolution, once your on I2P for a few hours,`
`  most peers will likely be able to find you by this Base32 hash of the Public Key.`
`  Standard I2P network Routers are not as likely to find your destination with it.`

The generated privatekey was automatically saved in I2Pkey.dat. Now you can start anoncoin using this static I2P destination by using this command:

`./anoncoind -i2p.options.enabled=1 -onlynet=i2p`

Alternatively, you can edit your own `anoncoin.conf` and add the privatekey and static in \[i2p.mydestination\]

`cp ../doc/anoncoin.conf.sample ~/.anoncoin/anoncoin.conf`
`nano ~/.anoncoin/anoncoin.conf`

See also
--------

-   [How to setup Anoncoin to use Tor](/How_to_setup_Anoncoin_to_use_Tor "wikilink")
-   [Securing your wallet](/Securing_your_wallet "wikilink")
-   [How to use a bootstrap file to speed up initial synchronization](/How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization "wikilink")
