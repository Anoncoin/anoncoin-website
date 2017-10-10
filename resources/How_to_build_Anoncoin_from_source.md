---
title: How to build Anoncoin from source
permalink: /How_to_build_Anoncoin_from_source/
---

Master 0.9.6.13
---------------

These guides are for installing the latest master builds (9.6.13) from [Github](https://github.com/Anoncoin/anoncoin). The new master version was released the 01/06/2017 with version ID **v0.9.6.13-979387d**. This version is based on Bitcoin 0.10.99 code.

**This version v0.9.6.13-979387d is the new official release build. FOr anci2pd the version is v0.9.6.13-06fddba**

Windows or OSX users can download version v0.9.6.12-3fd47af here: <https://github.com/Anoncoin/anoncoin/releases>

`anoncoin-0.9.6.12-win64-setup.exe Checksum: MD5 AC0B96AB335BE6E7E78B7D325AF4EBB3 SHA-1 DDB9A4BF777A870D874D872FCB381EF05FBF5E38`

Linux users can build master 0.9.6.12-3fd47af following those instructions below.

Antergos/Arch 64 bit
--------------------

For Arch, you will need to first enable the multilib repo, to pacman the lib32-qt4. Multilib is enabled by default in Antergos but not in normal Arch [1](https://wiki.archlinux.org/index.php/multilib).

`sudo pacman -S git`
`sudo pacman -S lib32-qt4`

Then continue with those commands:

`cd`
`git clone `[`https://github.com/Anoncoin/anoncoin.git`](https://github.com/Anoncoin/anoncoin.git)
`cd anoncoin`
`./autogen.sh`
`cd depends`
`` make -j`nproc` ``

The toolchain build will take half an hour or more depending processor and bandwidth, when it is over without error, on the prompt line type:

`dir`

One of the newly created directories is named after the 'triplet', for instance x86_64-unknown-linux-gnu, x86_64-w64-mingw32, i686-w64-mingw32, i686-pc-linux-gnu... : remember this as you will need to use it soon.

Now to configure the build of the Anoncoin executables, type the following line with <your triplet name> being the name of the 'triplet' directory quoted above (without &lt;&gt;).

`cd ..`
`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>

Finally launch the build while still in the /anoncoin/ directory:

`` make -j`nproc` ``

See below to recover the compiled binaries.

Ubuntu 64 bit or Debian 8
-------------------------

Open a terminal console and type:

`sudo apt-get update`
`sudo apt-get upgrade`
`sudo apt-get install g++ git automake`

Add those dependencies too:

`sudo apt-get install autoconf make libtool pkg-config libqt4-network libqtgui4`

You may need to install these other packages as well, but do so only if they misses at some point! : (Note, this will install ALL boost development packages)

`sudo apt-get install libboost-all-dev  git libdb++-dev libssl-dev`

Then continue with those commands:

`cd`
`git clone `[`https://github.com/Anoncoin/anoncoin.git`](https://github.com/Anoncoin/anoncoin.git)
`cd anoncoin`
`./autogen.sh`
`cd depends`
`` make -j`nproc` ``

The toolchain build will take half an hour or more depending processor and bandwidth, when it is over without error, on the prompt line type:

`dir`

One of the newly created directories is named after the 'triplet', for instance x86_64-unknown-linux-gnu, x86_64-w64-mingw32, i686-w64-mingw32... : remember this as you will need to use it soon.

Now to configure the build of the Anoncoin executables, type the following line with <your triplet name> being the name of the 'triplet' directory quoted above (without &lt;&gt;).

`cd ..`
`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>

If you want to build without the GUI, pass this argument to configure too : `--without-gui`

Finally launch the build while still in the /anoncoin/ directory:

`` make -j`nproc` ``

Now you can recover the compiled binaries (below).

**In case of sse2 related errors after typing make**, run this command:

`export CFLAGS=`“`-msse2`”` ; export CPPFLAGS=`“`-msse2`”` ; export CXXFLAGS=`“`-msse2`”

and then

`make clean`

Now do again

`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>
`` make -j`nproc` ``

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

Now jump to *What do do next?* section [How_to_build_Anoncoin_from_source\#What_to_do_next.3F](/How_to_build_Anoncoin_from_source#What_to_do_next.3F "wikilink")

Ubuntu 32 bit
-------------

Do the same as for 64 bit (see above). **But In case of sse2 related errors after typing the second make command in anoncoin directory**, run this command:

`export CFLAGS=`“`-msse2`”` ; export CPPFLAGS=`“`-msse2`”` ; export CXXFLAGS=`“`-msse2`”

and then

`make clean`

Now do again

`` ./configure --prefix=`pwd`/depends/ ``<your triplet name>
`` make -j`nproc` ``

You get the three binaries needed to run the wallet. Follow the 64 bit guide for how to install them in more convenient folders.

Windows build using Ubuntu 64 bit in a VM (VirtualBox)
------------------------------------------------------

Precompiled builds can be downloaded (version v0.9.6.12-3fd47af) here: <https://github.com/Anoncoin/anoncoin/releases>

`anoncoin-0.9.6.12-win64-setup.exe Checksum: MD5 AC0B96AB335BE6E7E78B7D325AF4EBB3 SHA-1 DDB9A4BF777A870D874D872FCB381EF05FBF5E38`

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
`` make -j`nproc` HOST=x86_64-w64-mingw32 ``

After the toolchain has been constructed, now build Anoncoin with your new prefix:

`cd ..`
`` ./configure --prefix=`pwd`/depends/x86_64-w64-mingw32 ``
`` make -j`nproc` ``
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
`cd anoncoin `

Next generate the make files using

`./autogen.sh`

Now, change to the directory 'depends' to start building the required dependencies

`cd depends`
`./config.guess`

This last command should output a triplet that looks something like this: x86_64-apple-darwin13.4.0. Enter (changing the triplet if necessary)

`` make -j`nproc` HOST=x86_64-apple-darwin14.3.0 ``

The dependencies should download and build. If there are no errors, continue to building the anoncoin binaries:

`cd ..`
`` ./configure --prefix=`pwd`/depends/x86_64-apple-darwin14.3.0 ``
`` make -j`nproc` HOST=x86_64-apple-darwin14.3.0 ``
`make check`
`make install`

The binaries `anoncoind`, `anoncoin-cli`, and `anoncoin-qt` should be located in the directories src and src/qt. To make an OSX application file, use

`make deploy`

This will create `Anoncoin.app` and `Anoncoin.dmg` in the the root anoncoin directory.

On first execution, if the directory `~Library/Application\ Support/Anoncoin` contained a blockchain from a previously installed version, execute

`anoncoin-qt -reindex`

Ubuntu 64 bit or Debian 8 - Without toolchain
---------------------------------------------

If you want to build `anoncoind` and `anoncoin-cli` without using the toolchain.

`sudo apt-get update`
`sudo apt-get upgrade`
`sudo apt-get install g++ git automake`
`sudo apt-get install autoconf make libtool pkg-config libqt4-network libqtgui4`

After the dependencies got installed, download anoncoin and configure the building process.

`cd`
`git clone `[`https://github.com/Anoncoin/anoncoin.git`](https://github.com/Anoncoin/anoncoin.git)
`cd anoncoin`
`./autogen.sh`
`./configure`

If you encounter any error.

`sudo apt-get install libboost-all-dev git libdb++-dev libssl-dev`

If you encounter *configure: error: libdb_cxx headers missing*.

`sudo add-apt-repository ppa:bitcoin/bitcoin`
`sudo apt-get update`
`sudo apt-get install libdb4.8-dev libdb4.8++-dev`

Now launch the configure again.

`./configure`

If you want to compile the GUI (`anoncoin-qtc`). After “make”, `anoncoin-qtc` will be found in `src/qt/`.

`sudo apt-get install libqt4-dev libprotobuf-dev protobuf-compiler`
`./configure --with-gui=qt4`

Now after a succesful configure ending, launch the build.

`` make -j`nproc` ``

You now have built `src/anoncoind`, `src/anoncoin-cli` and maybe `src/qt/anoncoin-qtc`.

The executables are quite big because they are built with GCC and you can strip the debug symbols, which reduces the executable size by about 90%.

`strip src/anoncoind`
`strip src/anoncoin-cli`
`strip src/qt/anoncoin-qtc`

For the command line client, you can skip to the command line setup on the [first run](/How_to_build_Anoncoin_from_source#Anoncoind_and_anoncoin-cli_command_line_setup_first_run "wikilink"). For the qt-client GUI, check [What_to_do_next](/How_to_build_Anoncoin_from_source#What_to_do_next.3F "wikilink").

------------------------------------------------------------------------

**FACULTATIVE:** In case of libdb4.8-dev failure, Ubuntu and Debian have their own libdb-dev and libdb++-dev packages, but these will install BerkeleyDB 5.1 or later, which break binary wallet compatibility with the distributed executables which are based on BerkeleyDB 4.8. If you do not care about wallet compatibility and if the above three lines with libdb4.8 failed, install libdb5.1 and pass --with-incompatible-bdb to configure. Otherwise, go directly to the “*make*” step.

`sudo apt-get install libdb5.1++-dev`

As explained, if you use BerkeleyDB 5.1 you will encounter *configure: error: Found Berkeley DB other than 4.8*. **Warning if you do not compile using Berkeley DB version 4.8 the wallet will not be portable (incompatibility issues with other build using Berkeley DB version 4.8). Please backup your previous wallet just in case and know what you are doing.**

`./configure --with-incompatible-bdb`

Now after a succesful configure ending, launch the build.

`` make -j`nproc` ``

------------------------------------------------------------------------

Anoncoind and anoncoin-cli command line setup first run
-------------------------------------------------------

`Anoncoind` and `anoncoin-cli` will have been created in `anoncoin/src` folder. To run it the first time, with no previous datadir (if it exists from a previous version please remove everything in `~/.anoncoin` **but not wallet.dat**).

`mkdir ~/.anoncoin`
`cp doc/anoncoin.conf.sample ~/.anoncoin/anoncoin.conf`
`nano ~/.anoncoin/anoncoin.conf`

In anoncoin.conf, change `rpcuser`, `rpcpassword`

For clearnet-only comment `onlynet=i2p` and in `i2p.options` set `enabled=0`

For I2P-only uncomment `onlynet=i2p` and in `i2p.options` set `enabled=1`

For I2P and clearnet (mixed mode) comment `onlynet=i2p` and in `i2p.options` set `enabled=1`

For I2P router configuration and settings check [How_to_setup_your_Anoncoin_wallet\#Using_the_command_line_to_generate_a_random_anoncoin_address_and_run_anoncoind_with_I2P](/How_to_setup_your_Anoncoin_wallet#Using_the_command_line_to_generate_a_random_anoncoin_address_and_run_anoncoind_with_I2P "wikilink")

Execute `anoncoind` and `anoncoin-cli`

`src/anoncoind`
`src/anoncoin-cli getinfo`
`src/anoncoin-cli getchaintips`

What to do next?
----------------

-   [Download and install the I2P router](/I2P "wikilink").

<!-- -->

-   Before the first run, please remove everything in the %appdata%/anoncoin directory (windows) or the .anoncoin/ directory (linux) **except wallet.dat**. The old `anoncoin.conf` is not compatible and the windows setup will open an `anoncoin.conf.txt` at the end of installation, which shall be renammed `anoncoin.conf` and copied in `%appdata%/anoncoin`. Similarly for linux a `anoncoin.conf.sample` can be found in the `anoncoin/doc` directory and shall be copied to `.anoncoin/anoncoin.conf`.

<!-- -->

-   To automatically generate an I2P address, launch the I2P java router with SAM bridge enabled and default configuration, and execute (or run the “Generate I2P static privatekey” shortcut on windows):

`anoncoin-qtc -i2p.options.enabled=1 -onlynet=i2p -generatei2pdestination`

To run in I2P only mode, without anoncoin.conf file, execute (or run the “Anoncoin Core I2P-only” shortcut on windows):

`anoncoin-qtc -i2p.options.enabled=1 -onlynet=i2p`

The I2P address generated above will be used unless another one is specified in anoncoin.conf. Please also check [How_to_setup_your_Anoncoin_wallet\#Setting_up_your_client_to_use_I2P_.289.6.9.29](/How_to_setup_your_Anoncoin_wallet#Setting_up_your_client_to_use_I2P_.289.6.9.29 "wikilink").

-   To use the bootstrap.dat (https://anoncoin.net/downloads/bootstrap/)

If there is no `/home/username/.anoncoin/` or `%appdata%/anoncoin`, you can either:

- manually create it `mkdir ~/.anoncoin` and put the anoncoin.conf and bootstrap.dat in it, then I2P will be enabled by default from the anoncoin.conf (onlynet=i2p)

- alternatively, run anoncoin-qtc once with the I2P only mode and close it after one minute to let it create the Anoncoin data directory.

Then, place the `bootstrap.dat` file in the appropriate Anoncoin data directory: [How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization](/How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization "wikilink")

-   Create the `anoncoin.conf` file in the appropriate Anoncoin data directory:

[Sample_anoncoin.conf](/Sample_anoncoin.conf "wikilink") using [Anoncoin-0.9.6.12.conf](/Anoncoin-0.9.6.12.conf "wikilink") or [Anoncoin-clearnet-0.9.6.12.conf](/Anoncoin-clearnet-0.9.6.12.conf "wikilink")

-   Check the list of all anoncoin commands

[Anoncoin-cli_commands](/Anoncoin-cli_commands "wikilink")

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")