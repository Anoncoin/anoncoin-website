---
layout: page
title: Securing your wallet
permalink: /Securing_your_wallet/
---

Encrypting your Anoncoin wallet
-------------------------------

All of the private keys for your Anoncoin [public addresses](/Anoncoin_Address) are stored in a single file on your computer called `wallet.dat`. By default, your wallet file is not initially encrypted when you open the Anoncoin client for the first time. If anyone could access this unencrypted file on your computer, they could easily steal all of your coins. For this reason alone, it is strongly recommended that you encrypt *immediately* your wallet with a password. For increased protection, when your wallet is encrypted, you will be required to enter the password before making any transactions.

To encrypt your wallet, from the Anoncoin client menu “Settings”, choose “Encrypt wallet” and enter a **strong password**. Before you continue, verify that the wallet is in fact encrypted by looking for the closed-lock symbol in the bottom-right corner of the client window.

The importance of choosing a strong password needs to be emphasized. If someone accesses your wallet after it is encrypted, even though it is not immediately readable, the party could decide to launch a concerted offline attack to guess the wallet password by brute force. Such offline attacks are very different than trying to guess a password to an online web site: For most online accounts, your account will be blocked after a few wrong passwords have been entered. For an offline attack, however, the party could test millions of random passwords over a several month time period, without you ever knowing. The attacker could easily test every possible combination of letters for passwords that are less than about 10 characters long. These attacks make use of dictionaries and consider common character substitutions, such as a “1” for and “i”. See [this article](http://dansdata.com/gz140.htm) for information on how passwords are hacked.

The importance of encrypting your wallet file immediately also needs to be stressed. If your original unencrypted file is backed up by automatic backup software, the possibility exists that an intruder could access the backup of this unecrypted file. If this happens, the coins associated with any of the addresses in the unencrypted file could be stolen.

Backing up your wallet
----------------------

First, open the Anoncoin client and make sure that the blockchain is fully synchronized. This is not strictly necessary, but it will simplify things if you need to use the backed up file later.

Next, locate the file `wallet.dat` on your computer, which should be located in one of the following standard directories:

### Windows XP

```
C:\Documents and Settings\YourUserName\Application data\anoncoin
```
 
### Windows Vista, Windows 7 and Windows 8

```
C:\Users\YourUserName\Appdata\Roaming\anoncoin
```  

### Mac OS X

```
~/Library/Application Support/Anoncoin/
```

### Linux

```
~/.anoncoin/
```

Finally, copy the file `wallet.dat` to an external hard disk. That's it!

You should ensure that this backed up file is in a secure location. If an intruder found a copy of this file on a backup disk, they could attempt to mount an offline campaign to guess the encryption password.

It should be emphasized that the wallet file does not contain your coins, per se: It only contains the private keys to access the coins associated with your addresses on the Anoncoin blockchain. Thus, if you backup your wallet, later receive some coins to one of the addresses in the wallet, and then use the backup of your wallet at a later date, all of your coins will still be there. However, if after backing up your wallet you created a new Anoncoin address, this would not be in the backed up wallet file, and hence all coins sent to that address would be lost.

Restoring your backed up wallet
-------------------------------

To restore your backed up wallet to the Anoncoin client (either on the original computer, or to another), simply copy the backed up file to its default location, as noted above.

Using the same wallet on two computers
--------------------------------------

This can be done, but it can also be dangerous if you don't know what you are doing. Do so at your own risk!

In particular, if you create a new address on one computer, it will not be available on the other (at least until the two wallet files are synched). Things get tricky when sending coins. By default, the change of a transaction is sent to a newly created address that is different from the original sending address. If you do not realize this, and if you replace the wallet file with a backed up version, the coins associated with the change address will be lost. The address that the change is sent to can be changed by using [Coin control](/Coin_control) features, but coin control needs to first be enabled in the preferences settings.

See also
--------

-   [How to setup your Anoncoin wallet](/How_to_setup_your_Anoncoin_wallet)

External links
--------------

-   [On the h4xx0ring of p4sswordZ (DansData.com)](http://dansdata.com/gz140.htm)
