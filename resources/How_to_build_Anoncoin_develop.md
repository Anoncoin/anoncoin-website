---
layout: page
title: How to build Anoncoin develop
permalink: /How_to_build_Anoncoin_develop/
---

These guides are for installing the latest development builds (9.6.9) from [Github](https://github.com/Anoncoin/anoncoin). The new develop version is *0.9.6.9-6e80477*, branch gr_develop, commit 6e80477 (https://github.com/Anoncoin/anoncoin/commit/6e80477aee8843b8e32755d04416a1283596a76e). This version is based on Bitcoin 0.10.99 code. The old 9.4.4 develop version was *0.9.4.4-53469ee*, branch develop. To install Git through I2P please check [the Git I2P guide](http://git.repo.i2p/h/guide/setting_up_tunnels.html).

Ubuntu 64 bit or Debian 8
-------------------------

Open a terminal console and type:

`sudo apt-get update`
`sudo apt-get upgrade`
`sudo apt-get install g++ git automake`

If you are using Debian 8 add those:

`sudo apt-get install autoconf make libtool pkg-config libqt4-network libqtgui4`

You may need to install these other packages as well: (Note, this will install ALL boost development packages)

`sudo apt-get install libboost-all-dev libdb++-dev libssl-dev`

Then continue with those commands:

`cd`
`git clone `[`https://github.com/Anoncoin/anoncoin.git`](https://github.com/Anoncoin/anoncoin.git)
`cd anoncoin`
`git checkout 6e80477`
`./autogen.sh`
`cd depends`
`make`

The toolchain build will take half an hour or more depending processor and bandwidth, when it is over without error, on the prompt line type:

`dir`

One of the newly created directories is named after the 'triplet', for instance x86_64-unknown-linux-gnu, x86_64-w64-mingw32, i686-w64-mingw32... : remember this as you will need to use it soon.

Now to configure the build of the Anoncoin executables, type the following line with <your triplet name> being the name of the 'triplet' directory quoted above (without &lt;&gt;).

`cd ..`
`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>

Finally launch the build while still in the /anoncoin/ directory:

`make`

Now you can recover the compiled binaries (below).

**In case of sse2 related errors after typing make**, run this command:

`export CFLAGS=`“`-msse2`”` ; export CPPFLAGS=`“`-msse2`”` ; export CXXFLAGS=`“`-msse2`”

and then

`make clean`

Now do again

`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>
`make`

**Recovering the compiled binaries:**

Three programs were created:

`anoncoin/src/anoncoind`

`anoncoin/src/anoncoin-cli`

`anoncoin/src/qt/anoncoin-qtc`

If you would like to save the resulting executables, you can do the following:

`make install`

This will store your 3 binaries in your <prefix>`/bin` directory, for example: `/home/cs8m/anoncoin/depends/x86_64-unknown-linux-gnu/bin`

To allow anoncoin-qt to be executable from any directory, you can copy it to `usr/local/bin`:

`cd src/qt`
`sudo cp anoncoin-qtc /usr/local/bin`

Now you can install the i2pd router in the same system as explained in [How to setup Anoncoin to use i2pd in a VM on a Windows machine](/How_to_setup_Anoncoin_to_use_i2pd_in_a_VM_on_a_Windows_machine "wikilink")

Then you can continue by configuring the `/home/username/.anoncoin/anoncoin.conf` following the guide at [How to run Anoncoin](/How_to_run_Anoncoin "wikilink")

On first execution, if the directory `/home/username/.anoncoin/` contained a blockchain from a previously installed version, execute

`anoncoin-qtc -reindex`

Ubuntu 32 bit
-------------

Do the same as for 64 bit (see above). **But In case of sse2 related errors after typing the second make command in anoncoin directory**, run this command:

`export CFLAGS=`“`-msse2`”` ; export CPPFLAGS=`“`-msse2`”` ; export CXXFLAGS=`“`-msse2`”

and then

`make clean`

Now do again

`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>
`make`

You get the three binaries needed to run the wallet. Follow the 64 bit guide for how to install them in more convenient folders.

Windows build using Ubuntu 64 bit in a VM (VirtualBox)
------------------------------------------------------

(Additional material, on how to build Anoncoin for another HOST)

After having saved the previously generated 3 binaries in your <prefix>`/bin` directory, the working directory tree can be cleaned of all your files used to create that configuration (see above)...

`cd ~/anoncoin`
`make distclean`

In the following example, we will be using Windows 64 bit as the target host.

If you haven't already done so, be sure now to have installed the g++ compiler for your target machine type, in this case we need the mingw-w64 tools for developers installed. Additionally, if you desire a Windows setup.exe to be built, you need to install the nsis developer tool. It works well with our Anoncoin setup.nsi script to build reliable Windows install/uninstall packages.

`sudo apt-get install mingw-w64 nsis`

Then finally you can build the toolchain for that alternative:

`./autogen.sh`
`cd depends`
`make HOST=x86_64-w64-mingw32`

After the toolchain has been constructed, now build Anoncoin with your new prefix:

`cd ..`
`` ./configure --prefix=`pwd`/depends/x86_64-w64-mingw32 ``
`make`
`make install`

This will store your 3 binaries in your <prefix>`/bin` directory, in this case: `/home/cs8m/anoncoin/depends/x86_64-w64-mingw32/bin`

Note: After that final install step, an anoncoin setup.exe can be built for windows too as follow. From the ~/anoncoin/ directory:

`mkdir release/ `
`cp depends/x86_64-w64-mingw32/bin/*.exe release/`
`cd share/`
`makensis setup.nsi`

The `anoncoin-0.9.6.9-win64-setup.exe` and the executables will be found in `anoncoin/release` and can be copied to your windows 64 bit machine.

To create a shared folder with the host computer on VirtualBox 4.3.20 (change number if another version is used), install the add-on:

`wget `[`http://download.virtualbox.org/virtualbox/4.3.20/VBoxGuestAdditions_4.3.20.iso`](http://download.virtualbox.org/virtualbox/4.3.20/VBoxGuestAdditions_4.3.20.iso)` `
`sudo mount -o loop VBoxGuestAdditions_4.3.20.iso /mnt`
`cd /mnt`
`sudo ./VBoxLinuxAdditions.run `

In VirtualBox, create a shared folder with automount activated

You shall then add your own user name <username> to the vboxsf group to get access to the shared folder

`sudo adduser username vboxsf`

Restart the VM and you shall see the shared folder in `/media`. Put the binaries inside to copy them to your host machine.

So there you go, how to build Anoncoin for multiple targets on your linux machine.

OS X
----

Download the Anoncoin code and then change to the anoncoin directory using the commands

`git clone `[`https://github.com/Anoncoin/anoncoin.git`](https://github.com/Anoncoin/anoncoin.git)
`cd anoncoin`
`git checkout develop`

Next generate the make files using

`./autogen.sh`

Now, change to the directory 'depends' to start building the required dependencies

`cd depends`
`./config.guess`

This last command should output a triplet that looks something like this: x86_64-apple-darwin13.4.0. Enter (changing the triplet if necessary)

`make HOST=x86_64-apple-darwin14.3.0`

The dependencies should download and build. If there are no errors, continue to building the anoncoin binaries:

`cd ..`
`` ./configure --prefix=`pwd`/depends/x86_64-apple-darwin14.3.0 ``
`make HOST=x86_64-apple-darwin14.3.0`
`make check`
`make install`

The binaries `anoncoind`, `anoncoin-cli`, and `anoncoin-qt` should be located in the directories src and src/qt. To make an OSX application file, use

`make deploy`

This will create `Anoncoin.app` and `Anoncoin.dmg` in the the root anoncoin directory.

On first execution, if the directory `~Library/Application\ Support/Anoncoin` contained a blockchain from a previously installed version, execute

`anoncoin-qt -reindex`

See also
--------

-   Alternatively, to build without the toolchain:

`./autogen.sh`
`./configure --with-incompatible-bdb`
`make`

-   [Anoncoin Doxygen project](http://anoncoin.github.io/anoncoin/)

What to do next?
----------------

Place the `bootstrap.dat` file in the appropriate Anoncoin data directory: [How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization](/How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization "wikilink")

Create the `anoncoin.conf` file in the appropriate Anoncoin data directory: [Sample_anoncoin.conf](/Sample_anoncoin.conf "wikilink")

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")