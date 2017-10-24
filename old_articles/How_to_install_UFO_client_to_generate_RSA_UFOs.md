---
layout: old_page
title: How to install UFO client to generate RSA UFOs
permalink: /How_to_install_UFO_client_to_generate_RSA_UFOs/
---

**For Ubuntu 12.04 or higher**
------------------------------

1. Install node.js using Launchpad repo by Chris Lea :

`sudo apt-get install python-software-properties`
`sudo apt-add-repository ppa:chris-lea/node.js`
`sudo apt-get update`
`sudo apt-get install nodejs`

2. Check the npm version by using the following command:

`npm -v`

If npm is not installed then, you will get error saying “npm : command not found.” Otherwise, you will get the version number like 1.4.14.

To install npm use the following command :

` sudo apt-get install npm`

3. Install other dependencies:

`sudo apt-get install build-essential libgmp-dev gmp-ecm git nano`

4. Download the ufo client from git:

`git clone `[`https://github.com/Anoncoin/ufo_client`](https://github.com/Anoncoin/ufo_client)

5. Configure and install the ufo_client :

`cd ufo_client`
`npm config set registry `[`http://registry.npmjs.org`](http://registry.npmjs.org)
`npm install`

6. Edit your nick from new configuration file:

`(umask 077 && node index.js > ~/ufo_config.yml)`
`nano ~/ufo_config.yml      # edit your nick`

7. Get your nick and pubkey from the configuration file:

`egrep 'nick|pubkey' ~/ufo_config.yml`

8. Send the nick and pubkey to Gnos1s, via IRC chat at \#anoncoin, or by pm on Reddit using the url : <http://www.reddit.com/message/compose/?to=gnos1s>

9. Running with the generated configuration file (after your nick has been added to database):

`node index.js ~/ufo_config.yml`

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Zerocoin](/Category:Zerocoin "wikilink")