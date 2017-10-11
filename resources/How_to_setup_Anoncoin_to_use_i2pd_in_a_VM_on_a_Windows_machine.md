---
layout: page
title: How to setup Anoncoin to use i2pd in a VM on a Windows machine
permalink: /How_to_setup_Anoncoin_to_use_i2pd_in_a_VM_on_a_Windows_machine/
---

Download Oracle VirtualBox <https://www.virtualbox.org/wiki/Downloads>

Download Mint 17.1 MATE, <http://www.linuxmint.com/download.php>, choose the version that is compatible with your system (32/64 bits)

Install VirtualBox, create a new Virtual Machine (VM) based on Linux Ubuntu, allocate 2048 MB memory, VDI dynamic, all default options

Run it, select your Mint iso file, install Mint

Restart VM, log in and open terminal (right click on desktop) type:

`sudo apt-get install g++`

Run web browser and go to <https://github.com/PurpleI2P/i2pd>

Download the ZIP file <https://github.com/PurpleI2P/i2pd/archive/master.zip> (alternatively execute from home `git clone `[`https://github.com/PurpleI2P/i2pd.git`](https://github.com/PurpleI2P/i2pd.git), in this case it will install in /home/i2pd directory)

Open the download directory, right click and extract to home directory

In the terminal type:

`sudo apt-get install libboost-dev libboost-filesystem-dev libboost-program-options-dev libboost-regex-dev libcrypto++-dev libboost-date-time-dev`
`cd`
`cd i2pd-master`
`make`

Shutdown the VM

In VirtualBox, select the VM and click on network

Select bridge network and choose your network adapter

Allow promiscuity mode All and write your MAC ID

Restart the VM, log in and in terminal type:

`ping 192.168.1.55`

It shall reply 'From 192.168.1.xx Destination Host Unreachable' : 192.168.1.xx is your IP address on the local network

Now open your router configuration in your normal browser (address is often 192.168.1.1 or type `ipconfig` in windows console and look for “standard gateway”)

You have to find your DHCP setting and bind address 192.168.1.xx to a static address with MAC ID = the one you wrote from VirtualBox network option

When this is done, go in the VM and type in terminal:

`cd i2pd-master`
`./i2p -daemon=1`

It will display the version of i2pd, the data directory and the CMD parameters. Now type:

`cd ../.i2pd `

In this directory, from terminal type:

`nano i2pd.log`

Search in the file: Start listening TCP port zzzzz and Start listening UDP zzzzz

zzzzz is the port number which i2pd is listening to

Now go back in your router configuration page in your normal web browser

Forward the ports TCP and UDP zzzzz to 192.168.1.xx

Go in the VM, close nano (ctrl+X) and type

`pkill i2p`

Restart the VM, log in and in terminal type:

`cd i2pd-master`
`./i2p -daemon=1 -port=zzzzz -samport=7656`

Now i2pd is running in the background

To access the webconsole, go in your favorite browser and connect to 192.168.1.xx:7070

In Windows, open directory %appdata%/anoncoin/ (Win+R then type in the box %appdata%/anoncoin/)

In that directory, edit anoncoin.conf (for version 0.9.4) and change those lines:

`onlynet=i2p #(if only i2p is wanted and not ipv4, be sure to not have any addnode=ipv4 address remaining)`
`[i2p.options]`
`enabled=1`
`static=1 #(be sure to have defined the three keys of a static I2P address in [i2p.mydestination])`
`samhost=192.168.1.xx #(the static local IP address allocated to the VM in DHCP)`
`samport=7656`

Run anoncoin-qt

Wait until it open and then get connected (check the peers in debug windows, it can take from 5 min to 20 min)
