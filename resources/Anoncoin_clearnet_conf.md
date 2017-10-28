---
layout: page
title: Anoncoin clearnet configuration.
permalink: /Anoncoin_clearnet_conf/
---

Name this file anoncoin.conf and saved it in:

#### Windows: 
```
%appdata%/anoncoin   
```            
#### Linux/MacOS: 
```
~/.anoncoin
```     

#### anoncoin.conf
```
daemon=1
server=1
rpcuser=************USER***************       #Change it! (no need to remember)
rpcpassword=**************SECRETPASS********* #Change it! (no need to remember)  
paytxfee=0.0001

#rpcallowip=192.168.0.0/24
#rpcallowip=192.168.2.0/255.255.255.0
#rpcbind=192.168.2.55
#rpcconnect=192.168.2.55
#rpcwait=1
 
#rest=1 

#rpcssl=1
#rpcsslcertificatechainfile
#rpcsslprivatekeyfile
#rpcsslciphers
#rpcport=443

############ Running a version of ONLYNET:       
#If everything is commented out, then we are in mixed mode (clearnet only if [i2p.options] enabled=0)

#onlynet=i2p       # I2P-only enabled!
#onlynet=ipv4     # IPV4 disabled!
#onlynet=ipv6
#onlynet=tor
#onlynet=onion 


############ MISC Settings

#stopafterblockimport=1      # useful when using bootstrap.dat, to shutdown the qt-client when file-synching is done
#loadblock=/home/groundrod/.anoncoin/blocks-src/blk00000.dat #to use raw blk#####.dat instead of bootstrap.dat 

#bind=192.168.0.11   # set this node local-network address if you do a multi-nodes local network or for port-forwarding, else comment it!
#whitelist=192.168.0.11      #c hange this to another local node local-network address to allow it to connect!
#whitebind=192.168.2.55

#checkblocks=50000

#externalip=???
#connect=192.168.0.101    # only connect to this node 

#listen=1 # NOTE: Listen only refers to clearnet IPs, I2P always listens, if enabled.
#discover=0    # Try to discover our own IP address
#upnp=1    # enable upnp to open port for inbound connection on clearnet

#dns=0
#dnsseed=1
#forcednsseed=1

#stfu=1    # Tired of the 'running on clearnet warning' during startup?  Try this... 

#txindex=0    #enable it to use multisig transactions
dbcache=400   #larger peer address space supported by Anoncoin for I2P

############ Debugging Options

#checkblockindex=1
#checkmempool=1
#logips=1
#logtimestamps=0

#debug=    # enable ALL debug category except bench and estimatefee

#debug=addrman    # category specific debug log
#debug=alert
#debug=coindb
#debug=db
#debug=lock
#debug=gui
#debug=mempool
#debug=net
#debug=rand
#debug=retarget
#debug=rpc
#debug=rpcio
#debug=selectcoins
#debug=timedata
#debug=version

#debug=bench
#debug=estimatefee

############ Mining Options, enable TestNet and start a new one with initial conditions valid.

#keypool=100

#gen=0
#genproclimit=1

rpcport=9376  # The default MainNet RPC port
#rpcport=9377 # The default TestNet RPC port

#testnet=0
#testnetstart=0             # only one master per testnet! For the master it has to be testnetstart=1

#utctimeisknown=1


############ New RetargetPID parameter control and csv file logging options in this new [ ] section

[retargetpid]

# HARDCODED VALUES

retargetcsv=0

############ Anoncoin IP2 network Destination settings.

[i2p.mydestination]
static=1          # uncomment after having copied the "privatekey" parameter below
#privatekey=       # copy here the settings->I2P Destination details-> "privatekey" parameter and remove the #

shareaddr=1       # sharing of dynamic and static I2P address is enabled by default.

############ Anoncoin IP2 Options settings.

[i2p.options]
enabled=0             # here i2p is disabled for clearnet only mode, enable for i2p
samhost=127.0.0.1     # set to I2P-SAM local address of the I2P router, after enabling SAM in it
samport=7656
sessionname=Anoncoin-client
extra=

# Inbound parameters options
[i2p.options.inbound]
quantity=3
length=3
lengthvariance=0
backupquantity=0
allowzerohop=0
iprestriction=2 

# Outbound parameters options
[i2p.options.outbound]
quantity=3
length=3
lengthvariance=0
backupquantity=0
allowzerohop=0
iprestriction=2
priority=0
```