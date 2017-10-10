---
layout: page
title: How to import and export private keys from the Anoncoin client
permalink: /How_to_import_and_export_private_keys_from_the_Anoncoin_client/
---

Be extremely careful when importing or transferring private keys. You could loose all your coins if this is done improperly. Private keys should be imported only from self-generated addresses.�

How to import a private key
---------------------------

### Step 1. Open the RPC console in the Anoncoin client

Click on *Help*, open the *Debug Window* and switch to the *Console* tab.

### Step 2. Unlock your wallet

If your Anoncoin wallet is not encrypted (which is highly unadvised, please encrypt it now!) you can skip this step.

To unlock your wallet you need to type the following in the RPC console:

`walletpassphrase MyPassword 60`

Change `MyPassword` to your wallet passphrase and change `60` to the number of seconds that you want the wallet to be unlocked. After that time the wallet will be locked automatically. Make sure to unlock the wallet long enough to do the next and final step.

### Step 3. Import the private key

Type into the RPC console:

`importprivkey MyPrivateKey Label`

Change `MyPrivateKey` to your private key (which starts with `64`, `65` or `66`) and for `Label` you can enter a name/description/label for the key (optional). The importing takes a few minutes depending on your CPU power. The import is done when an empty line appears in the console. You should now be able to see the corresponding address to the imported key in the *Addresses* section of the client.

How to export a private key
---------------------------

Exporting a private key follows the same steps as above for importing a private key. For step three, instead type

`dumpprivkey MyAnoncoinPublicAddress`

Please store your private key in a secure location: If anyone obtained it, they would be able to steal all of your coins.

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")