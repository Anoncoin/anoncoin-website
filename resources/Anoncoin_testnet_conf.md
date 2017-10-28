---
layout: page
title: Anoncoin testnet configuration.
permalink: /Anoncoin_testnet_conf/
date: 2017-10-28
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
#anoncoin.conf
#
# True or False boolean parameter values should use 0 or 1 when setting the value in this configuration file.
#

daemon=1
server=1

# If your like me and run QT...and tired of the many invalid 509 root certificate warnings that show up in
# your debug.log, try this...

rootcertificates=

# First up,
############ Using and running the RPC Server!
# Dont use rpcallowip(s) with 127.?.?.? addresses, the software defaults to granting all local machine
# loopback adapters access.

rpcallowip=192.168.0.0/24
#rpcallowip=192.168.2.0/255.255.255.0
#rpcallowip=192.168.2.12
#rpcallowip=192.168.2.16

# This bind seems to work great for the rpc, gives it a static presence on your local network.

#rpcbind=192.168.2.55
rpcuser=************USER***************
rpcpassword=**************SECRETPASS*********

# These are for the anoncoin-cli client, rpcwait causes the warmup cycle to complete, before
# a command returns with the response. rpcconnect tells cli where to find the server. 

#rpcconnect=192.168.2.55
#rpcwait=1

# A new built-in public rest server is ready for Browser access to the node's blockchain and transactions data!
#rest=1

# Plus it can respond to you in binary, hex or JSON!
# Simple examples from a browswer line & using a valid local network IP addresses are shown: 
# http://192.168.2.55:9376/rest/tx <transaction hash>.json or .hex or .bin
# http://192.168.2.55:9376/rest/block <hash-either scrypt or sha256d should work>.json or .hex  or .bin
# Here is a complete example (using the 3rd & last rest command) with a recent real anc block scrypt hash:
# http://192.168.2.55:9376/rest/blocknotxdetails 00000000012a8a37700197a1f2cb3d8cb868d9754d6a65839687ddad37bdf856.json
# by placing the .json at the end, it will return to me a JSON response result.
#
# The 'rest' interface uses the same port # as whatever you have configured for the other RPC functionality.
# If public access to the server is to be allowed from any browswer url without the user needing to specify
# the port #, you would have to run your node with the RPC port number specified and set to the standard
# http port of 80 as follows. #rpcport=80 


# Doing that opens up additional security concerns however, so the system supports the use of another option,
# allowing you to operate over https:// type connections, the standard default is port 443, again any other
# you have setup or choose is fine. SSL type connections use some additional paramaters which are processed
# as part of our initialization.  The 1st enables the feature, the next 2 reference certificate files you must
# have setup and the rpcsslciphers option specifies the ciphers, our default is:
# "TLSv1.2+HIGH:TLSv1+HIGH:!SSLv2:!aNULL:!eNULL:!3DES:@STRENGTH"

#rpcssl=1
#rpcsslcertificatechainfile
#rpcsslprivatekeyfile
#rpcsslciphers
#rpcport=443

############ Running a version of ONLYNET:

onlynet=i2p       #I2P-only enabled!
#onlynet=ipv4     #IPV4 disabled!
#onlynet=ipv6
#onlynet=tor

############ MISC Settings
#
# Example here of how to import an old good copy of the blockchain, there are only 3 files needed,
# before long there will be four as time marches on, but atm there are only 3 files with all the
# Anoncoin blocks and transactions in them that are needed, beside your wallet.dat file.  These
# can be used to re-create a new working blockchain and index, if an old wallet.dat file is found
# it will be used and the transactions verified as the blockchain is re-created and loaded into
# the new software.
# Delete everything else in your <datadir path>/blocks and <datadir path>chainstate directories
# Except for the 3 files which have the blocks in them.  They will be named blk00000.dat,
# blk000001.dat and blk00002.dat and found in the /blocks folder.
# Rename your old /blocks directory to /blocks-src  Then you can simply uncomment these next lines
# and use them as is, although I doubt your datadir path is same as mine, and the rest of the path
# is what would be needed for a linux box as the default location.  The concept is the same for all
# the OS flavors we support.

#loadblock=/home/groundrod/.anoncoin/blocks-src/blk00000.dat
#loadblock=/home/groundrod/.anoncoin/blocks-src/blk00001.dat
#loadblock=/home/groundrod/.anoncoin/blocks-src/blk00002.dat

# This works great for having the software exit after a clean load.  Don't forget to turn it off
# after your done though. 

#stopafterblockimport=1      #useful for first bootstrap, to shutdown the qt-client when file-synching is done

# NEW whitelist and whitebind options allow for local network multi-node setups.  Have not yet used
# whitebind. However whitelist means other machines on my network, with those addresses can connect
# too.

whitelist=192.168.0.11      #change this to another local node local-network address to allow it to connect!
whitelist=192.168.0.19
whitelist=192.168.0.20
whitelist=192.168.0.21
#whitebind=192.168.2.55

# Software auto checks 980 blocks at level 3, and it does not take long, so do not recommend you
# change the following, although it is an option and in some cases you may want to test allot more.

#checkblocks=50000

# Set bind if you want, works for me and this is related to the peer-to-peer network now, not the RPC.
# This does not effect what IP address you will be known by with peers, it allows you to bind with
# a local network adapter address, instead of the default loop-back adaptor and thus allow connections
# with other peers you may have on a local network, as well as solving problems with routers and
# firewalls that maybe setup to port forward to you, in such cases you need to specifically bind to
# your interal networks configured IP address, so that you can receive those inbound connections from
# the outside world.  Many never get inbound connections working, because of forgetting this one last
# step, or not understanding how to set up that port forwarding in their router, that is explained in
# great detail and made easy for nearly everyone with the help from: http://portforward.com/

#bind=192.168.0.11   #set this node local-network address if you do a multi-nodes local network or for port-forwarding, else comment it!

# NOTE: externalip will not override IsRoutable(), while trying to define it as a local IP address,
# so it is unusable for anything other than outside world valid IPv6 or IPv4 addresses, which some
# folks may need and very well want to specify as their IP address, this has long been in our config
# files, but poorly understood.

#externalip=???
 
# New optional connect=
# This allows you to run with no outbound connections.  In fact the thread running that process is
# shutdown, if you follow it by a listen=0, all clearnet IP listening will be disabled too.   Your
# log can be free to record other activities, that is what we use it for, although it can also be
# used while doing a complete blockchain load from files, or using the bootstrap.dat to start out
# your blockchain from the last defined Checkpoint.  Uncomment the next line to achieve that.

#connect=

# This next line would cause it to connect to only one other peer on a local network.

#connect=192.168.0.101

# NOTE: Listen only refers to clearnet IPs, I2P always listens, if enabled.

listen=1
#discover=0

# Forcing discover=0 above ensures you that the software will not 'try' to find the public address of your local
# machine or network, normally you might think that means this machine will not try to advertise itself with a
# clearnet IP address, and it could be used to connect to any local IP address which may have it whitelisted.
# However it is far from being that simple, discover can be left as undefined, and defaults to a value based
# on other settings, so depending on that outcome you may want to define it specifically here, or let it default.
# Besides UPNP, there are 2 service sites from which an attempt is made to obtain your IP address, if this is
# enabled, and while not operating in an I2P only mode.  If all of those fail, it still gathers information about
# what your IP address is from the clearnet peers it is connected to.  This is done during the initial version
# message exchange, and if it is an inbound connection then that carries allot of weight in the decision process.
# If you are trying to run a local network, with this machine as a local only peer and have another machine setup
# as a gateway, then you would want to have discover=0 set here and likely listen=0 as well, forcing it to connect
# to that gateway machine only, so that you do not have it broadcasting a clearnet IP that you did not what it to
# know about in the first place.  Be sure to also delete your peers.dat file when setting up these type of
# configurations, otherwise you maybe surprised to find it still has figured out your external IP address and
# started making connections with peers outside the network, it is relentless in its attempt to connect!

# UPNP is something you may or may not have setup to ensure the software knows what your correct IP address is.
# This next option enables that or disallows 'discover' use it as one of the processes in that discovery, many
# users will want it to be set true (upnp=1), it all depends on how you have your local equipment setup.

upnp=0

# ToDo: there is still some strange QT build interaction with its settings that needs to be looked into regarding
# the upnp option, the thread has been found running, even though this setting is set to false(0) here in the
# configuration file, unless it is specifically also set to false in the QT build settings page.

# ToDo: more documentation...
#dns=1
#dnsseed=0
#forcednsseed=1

# Tired of the Clearnet warning on startup?
stfu=1

# ToDo: more documentation...
txindex=0
dbcache=400

############ Debugging Options
# This is a major new way to turn on nearly ALL debugging, follow the parameter by an equal sign, and nothing more:

debug=

# A debug option specified as debug=1 is not longer supported, there is no such catagory defined, and effectively
# turns off debugging.  ToDo: Detect that, and note it in the log.  The options now come in many catagories, and
# they are listed below, it is not simply a true or false setting, although I have made the coding changes so that
# it is possible to turn nearly all of them on with one line.  It must be defined without a value indicated, as
# shown above.

# Turning this next one on really slows down the software, mine to ~4 blocks/sec and had to abort the bootstrap.dat
# import, however no errors where reported out past bock #80K+  If turned on, allot of details about block processing
# is constantly being checked and analysed by the software and can be a helpful debugging tool, but not if 350K+
# blocks need to be loaded.

#checkblockindex=1

# Monitoring the mempool operational status has often been a good idea, this allows you to confirm its status
# and will produce entries within the log periodically when turned on:

#checkmempool=1

# logips now has much power over private ip/i2p information logging, there are still a few placing in the code,
# such as during the p2p version message exchange, and other node and message processing sections where this
# flag is not yet being checked and they are still logged regardless of the setting, but for the most part you
# can now disable IP/I2P details from appearing in the debug.log output, or enable them whichever you prefer by
# using the following option.  IP addresses and I2P destinations are not really needed in most cases for debug
# log analysis, particularly when being shared between users to help one another figure out what is wrong. In
# some cases the user maybe reluctant to share what is potentially a personal security risk to them, or at the
# very least contains allot of rather sensitive and private details they would prefer was not shared.  This
# effort reduces all that detail to a set of Node ID #'s and means that nearly a complete removal of IP/I2P
# details from the debug.log file is possible while this option is turned off.  It is a work in progress towards
# that goal.

logips=1 

# You may not want even time stamps in the debug.log either, this is how you turn them off:

#logtimestamps=0

# The current list of catagory specific debug options are as follows: 
#debug=addrman
#debug=alert
#debug=coindb
#debug=db
#debug=lock
#debug=net
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

# These next two take up allot of lines, and are off by default, even if
# debug= has been set, they can only be turned on by explicitly including
# them in the categories you want to debug. 

#debug=bench
#debug=estimatefee

# ToDo: documentation on the debug catagories, some are newly created and others greatly enhanced.

############ Mining Options, enable TestNet and start a new one with initial conditions valid.
#
# Mining should now work for both the Main network using the old KGW retarget system, or after
# we hardfork the blockchain, testnets exclusively use the retargetpid for operational testing.
# This is what you should see in your debug.log file now when mining is turned on:
#
# AnoncoinMiner v2.0 for Scrypt started...
# ...with (DDA) Dynamic Difficulty Awareness and (MTHM) Multi-Threaded HashMeter technologies.

keypool=200

gen=0                   #CPU Mining is OFF!
genproclimit=1		#Number of Core to mine!

# The default MainNet RPC port:
#rpcport=9376
rpcport=9377 #testnet

# TestNets can be started and/or created new from scratch by adding these config file settings.

#testnet=1
testnet=0

# This next parameter allows you to creates a new testnet, with a default condition of the
# genesis block, followed by mocktime blocks created in the most recent past, spanning one
# complete 'tipfilterblocks' number of entries.  It takes some time to create, although an
# attempt is made to create the last block only seconds ago in realtime when built. The idea
# is to immediately connect with at least one peer, and start out mining real testnet blocks
# at whatever you have set for the starting difficulty which works best.
# This option allows a master testnet creator to start out a new block chain.  Peer(s) can
# then normally download, without this parameter set & it defaults to being disabled.  Once
# initialized this value is also no longer considered by the node which orignally created 
# the mocktime blocks, unless all the block and chainstate files are deleted.

testnetstart=0             #only one master per testnet! For the master it has to be testnetstart=1

# Headers can not be included, until the coin network demands and has precise control over what peer
# clocks think UTC time really is.  Allowing blocks to have a future time more than mere seconds
# invalidates the idea of using Header block time in current error calculations.  The RetargetPID
# fully supports the idea however, and we would like to include it in future Anoncoin designs.
# You can turn on the 'useheader' parameter defined below in the [retargetpid] section, and run
# a testnet for yourself to observe the results, they are impressive as to how smooth spacing
# can become.
#
# One exploit used by attackers is to adjust the clocks on miner nodes, this can be by as much as
# 70 minutes based on old btc code.  This could easily be stopped with a new anoncoin.conf file
# setting that you find here next.  It indicates the user (you-a miner or anyone really) has taken
# control of what the real UTC time your machine is set to.  Setting this option does not mean 
# the software believes you though, you STILL must have peer concenses with the network time
# or it will keep bugging you to fix the clock problem, so do not lie to it! If you are unsure
# the computer this is to be run on has the correct UTC time, let the adjustments be made by your
# peers, most often it is only by a few seconds and helps to keep everybody in agreement.
# Setting this parameter to true, enables you the user to become responsible for the systems
# correctly set UTC time, and stops peers from being able to adjust your sense of network time.
# Thus:
# IF you do know what the real UTC time is, and have your computer set to it, by all means:

#utctimeisknown=1


############ New RetargetPID parameter control and csv file logging options in this new [ ] section

[retargetpid]

# The tipfilterblocks setting can now be any value, even or odd, but is forced to be at least 5 blocks.
# Testnets can be run with many possible different values to analyse the results and calculate new and 
# different P, I and D term gains based upon them. 

# The later, now replaces the above 2 header item options, as the dtermheader can not be included
# if the ptermheader has not been calculated, so it seemed pointless to have two settings, it must
# be both or neither. Also plans are for the HARDFORK builds to have it default to false(0), until
# we can have solid peer agreement on what time really is universally, this can not be allowed to
# be true(1) for anything other than a testnet.  It is allowed to be either for all networks as the
# software is built right now in v0.9.6.9

# This next one allows the testnet builder to start difficulty out a some predefined value, the
# integer whole positive number is divided into the networks minimum difficulty and the 256 bit
# number produced placed into all the mocktime blocks required to build the TipFilter when first
# initializing a new testnet.


# Maxdiffincrease and maxdiffdecrease values need to be positive integers greater than or equal to 101, 
# both operate on the previous difficulty.  They are written in hundredths (percent multiplier and percent 
# divider respectively) and not in units, thus to limit the increased next difficulty to x 2, 200 
# shall be set for maxdiffincrease. A maxdiffdecrease=200 equal half. The increase is a divider, and 
# the decrease is a multipler to whatever the previous difficulty is defined as.  Those values define 
# the upper and lower bounds of change that is allowed to the next work required and MUST be a single 
# whole integer value, in fact representing a percentage. 
# The 'limitfromprevblock' parameter below allows to redefine which 'previous difficulty' is used to
# do the PID calculus. The default is the very last blocks difficulty, which cause a large velocity of 
# change which is allowed when limits are being hit. The setting 'limitfromprevblock=0' use the
# smoothed value obtained from the tipfilter.
# Proportionalgain and derivativegain are self explanatory, although the low resolution of block to 
# block calculation preclude setting derivativegain to anything other than 0 for useheader=0. Later, 
# when useheader=1 can be set through the use of a consensus time mechanism, it can be useful.
# Integrationtime is the length of time (in seconds) integrated and divided by the number of blocks
# to calculate the mean of all block times (integratorblocktime). 
# Integratorgain is the multiplier of the (signed) difference between the integratorblocktime and
# the targetspacing (180 sec). Fine tuning of the PID can thus be done using all those parameters.


tipfilterblocks=31  
useheader=0


proportionalgain=2.5
integrationtime=432000
integratorgain=4
derivativegain=0

startingdiff=200
maxdiffincrease=200
maxdiffdecrease=200

#limitfromprevblock=1

#define DMININTEGRATOR 170 #not a parameter, has to be set manually in pow.cpp, anti wind-up
#define DMAXINTEGRATOR 190
#define WEIGHTEDAVGTIPBLOCKS_UP 4 #not a parameter, has to be set manually in pow.cpp, Moving averages
#define WEIGHTEDAVGTIPBLOCKS_DOWN 6 

#define WEIGHTEDAVGTIPBLOCKS_UP 12 #not a parameter, has to be set manually in  
#define WEIGHTEDAVGTIPBLOCKS_DOWN 20 
 
# The primary P-I-D controller values, these are for the current testnet being run, once defined
# they will be hard coded into the software for a HARDFORK build and only available as options
# for a testnet.  Main net values will be locked.  ATM my intention is to set the locked values
# for P and D to those shown here, and the integrationtime=1209600 (2 weeks). 


# More sample PID settings that have been under test and evaluation
#derivativegain=0.0
#integrationtime=1209600 2 weeks
#integrationtime=604800 1 week
#integrationtime=86400 24hrs
#integrationtime=129600 36hrs
#integrationtime=28800
#integrationtime=21600 3600 x 6hrs
#integrationtime=10800 
#integrationtime=7200
#integrationtime=3600

# If the following parameter -retargetpid.logallblocks is not set, the default is to only log blocks > the
# last checkpoint, For Testnet this is block 0, but for MainNet retarget.csv grows so large this was added.
# If set true, all block and retarget data from genesis will be modeled to the csv file.  As allot of data
# can be output and time taken to produce the retarget.csv the -retargetpid.enablecsv parameter allows you
# to turn the generation of the retarget.csv on, all of these output options now default to off, except the
# new one recently added and defaulting to on is 'logdifflimits', for which 3 columns will be added to the
# retarget.csv file, so that limits can be evaluated and tested.  After that is done, they can be turned off
# with that new log setting.  diffcurves only applies to testnets where the 'useheader=1' is set.

retargetcsv=1
#logdifflimits=0
#diffcurves=1
#logallblocks=1

############ Anoncoin IP2 network Destination settings.

[i2p.mydestination]
#static=1          #uncomment after having copied the "privatekey" parameter below
#privatekey=       #copy here the settings->I2P Destination details-> "privatekey" parameter

# The next option allows dynamically created I2P destinations to be shared, although in most cases
# we do not what that to be done, only statically defined I2P destinations are shared by default.

shareaddr=1

############ Anoncoin IP2 Options settings.

[i2p.options]
enabled=1
samhost=127.0.0.1
samport=7656
#samhost=192.168.0.103
#samport=7657
sessionname=Anoncoin-client
extra=

# Inbound parameters options
[i2p.options.inbound]
quantity=3
length=3
lengthvariance=0
backupquantity=1
allowzerohop=0
iprestriction=2

# Outbound parameters options
[i2p.options.outbound]
quantity=3
length=3
lengthvariance=0
backupquantity=1
allowzerohop=0
iprestriction=2
priority=0
```