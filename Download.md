---
layout: page
title: Downloads
permalink: /Download/
---

Last official release July 13, 2018
---------------------
<a name="windowsdownload"></a>
-   Version 0.9.7
-   Release date: July 13, 2018
-   [Github release](https://github.com/Anoncoin/anoncoin/releases)

--------
## Windows
__[Download Anoncoin Core 0.9.7 for Windows.](https://github.com/Anoncoin/anoncoin/releases/download/v0.9.7-gost/anoncoin-0.9.7.0-win64.zip)__
- Save and unzip the archive, chose "keep file" if asked.
- Double-click / open the archive.
- Click "More info" if asked and chose "Run anyway" and click "Yes".
- Install and then open "Anoncoin Core (64-bit) Classic to run on clearnet.
<a name="macdownload"></a>
If you want to use I2p you can run "Generate I2P static privatekey" and [follow the instructions here.](/How_to_setup_your_Anoncoin_wallet)


--------
## MacOS
__[Download Anoncoin Core 0.9.7 for MacOS.](https://github.com/Anoncoin/anoncoin/releases/download/v0.9.7-gost/anoncoin-0.9.7.0-macOS.dmg)__
- Double-click the downloaded file.
- Drag "Anoncoin" into "Applications".
- Right-click the "Anoncoin" application and chose "open".
<a name="linuxdownload"></a>
If you want to use I2p you can generate I2P static privatekey and [follow the instructions here.](/How_to_setup_your_Anoncoin_wallet)


--------
## Linux

Clone the master from [the git repository](https://github.com/Anoncoin/anoncoin), it contains all the source files needed to compile your own binaries. 

### Quick howto for Ubuntu

```
sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install g++ git automake autoconf make libtool pkg-config libqt4-network libqtgui4 libboost-all-dev
git clone https://github.com/Anoncoin/anoncoin.git
cd anoncoin
./autogen.sh
cd depends
make -j`nproc`
cd ..
./configure --prefix=`pwd`/depends/x86_64-unknown-linux-gnu
make -j`nproc`
```

For more information you can read the guide on [how to build Anoncoin from source](/How_to_build_Anoncoin_from_source/). Binaries are in the works for multiple Linux distributions.


--------

## Mobile

Mobile wallet support will come with the release of Anoncash 

--------

## Source Code

Obtain the Anoncoin source code by [cloning the git repository](https://github.com/Anoncoin/anoncoin).

Anonymous download of these files is possible using the [Anoncoin I2P git repository](http://git.repo.i2p/w/anoncoin.git).