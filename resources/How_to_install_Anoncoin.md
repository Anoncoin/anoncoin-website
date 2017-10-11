---
layout: page
title: How to install Anoncoin on Windows
permalink: /How_to_install_Anoncoin/
---

Installation on Windows
-----------------------

After having downloaded the extractable zip file ([Download](/Download)), execute the included anoncoin setup. 

![Image](/img/Welcome_setup.PNG) 

Choose the installation folder. 

![Image](/img/Install2.PNG)

Choose the start menu folder.  

![Image](/img/Install3.PNG) 

Complete the installation.  

![Image](/img/Install4.PNG) 

If you have the [I2P](/I2P) router already configured ([How_to_install_and_use_I2P](/How_to_install_and_use_I2P)), this is excellent and you shall generate an I2P static key by checking the box.  

![Image](/img/Install5.PNG) 

If the box was checked, Anoncoin-qtc will connect to the I2P router using the default configuration and generate a new I2P destination. At the same time the `anoncoin/doc/anoncoin.conf.txt` will open for further configuration. By choosing **Abort** you will stop the configuration using the `anoncoin.conf` but can still run Anoncoin-qtc in I2P-only mode using the “Anoncoin Core (64-bit) I2P-only” link, in this case the I2P destination saved in the `I2Pkey.dat` file will be used instead of the one from `anoncoin.conf`. By choosing **Apply** on the *Anoncoin - Generated I2P Destination* box, Anoncoin-qtc will open and display your Private I2P Destination Details.  

![Image](/img/Install6.PNG) 

In the *Private I2P Destination Details* windows, you can easily copy your private key by clicking on the button **Copy “Privatekey” parameter to the clipboard**.  

![Image](/img/Install7.PNG) 

You shall then paste the Privatekey to the appropriate section of anoncoin.conf.txt  

![Image](/img/Install9c.png)

Then you shall set a new RPCuser and RPCpassword that are difficult to guess.  

![Image](/img/Install9.png) 

Finally, you can choose to run Anoncoin in `onlynet=i2p`, in `onlynet=ipv4` or in both network by commenting every line. The onlynet are additive so you can run tor and i2p at the same time.  

![Image](/img/Install9b.png) 

Save `anoncoin.conf.txt` into `%appdata%/anoncoin/anoncoin.conf`. Do not forget to rename it by removing the txt extension! The correct name is `anoncoin.conf`  

![Image](/img/Install9d.png) 

Now that it is properly configured, Anoncoin is now ready to be run in the classic mode. Do not hesitate to try more options in `anoncoin.conf`!  

![Image](/img/Install9e.png) 

On first launch, because of the way the Header-First synchronization is going, the block download can seems to stop. If you want to check what is going on, you can type `getchaintips` in the debug console. The Block headers are first downloaded and verified (status:“headers-only”), which takes almost two hours, then the blocks are downloaded from all the connected peers in parallel, increasing the status:“active” chain. If you use the `bootstrap.dat` ([How to use a bootstrap file to speed up initial synchronization](/How_to_use_a_bootstrap_file_to_speed_up_initial_synchronization)) then you will at first only see one chain because using this linearized bootstrap both block headers and block data are verified simultaneously, then it will catch-on the current tip using the Header-First synchronization.  


![Image](/img/Install9f.png)