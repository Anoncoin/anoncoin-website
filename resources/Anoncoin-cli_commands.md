---
layout: page
title: Anoncoin-cli commands
permalink: /Anoncoin-cli_commands/
---

The following commands are to be typed in the Help -&gt; debug -&gt; console in anoncoin-qtc or else at the command line to anoncoin-cli, after having started anoncoind

{% highlight shell %}

./anoncoind
Anoncoin server starting
./anoncoin-cli help

{% endhighlight %}



This is the list of all commands:

{% highlight shell %}

== Blockchain ==
getbestblockhash
getblock <“hash”> [verbose]
getblockchaininfo
getblockcount
getblockhash <index>
getchaintips
getdifficulty
getmempoolinfo
getrawmempool [verbose]
gettxout <“txid”> <n> [includemempool]
gettxoutproof <“txid”,...> [blockhash]
gettxoutsetinfo
verifychain [checklevel] [numblocks]
verifytxoutproof <“proof”>
== Control ==
getinfo
help [“command”]
stop
== Mining ==
getblocktemplate [“jsonrequestobject”]
getgenerate
gethashmeter [clear]
getmininginfo
getnetworkhashps [blocks] [height]
getretargetpid [height] [verbose]
getwork [“data”]
prioritisetransaction <txid> <priority delta> <fee delta>
setgenerate <generate> [genproclimit]
submitblock <“hexdata”> [“jsonparametersobject”]
== Network ==
addnode <“b32.i2p|base64|ip:port|ipv6”> <“add|remove|onetry”>
destination [“match|good|attempt|connect”] [“b32.i2p|base64|ip:port”]
getaddednodeinfo <dns> [“node”]
getconnectioncount
getnettotals
getnetworkinfo
getpeerinfo
ping
== Rawtransactions ==
createrawtransaction [{“txid”:“id”,“vout”:n},...] {“address”:amount,...}
decoderawtransaction <“hexstring”>
decodescript <“hex”>
getrawtransaction <“txid”> [verbose]
sendrawtransaction <“hexstring”> [allowhighfees]
signrawtransaction <“hexstring”> ( [{“txid”:“id”,“vout”:n,“scriptPubKey”:“hex”,“redeemScript”:“hex”},...] [“privatekey1”,...] sighashtype )
== Util ==
createmultisig <nrequired> <[“key”,...]>
estimatefee <nblocks>
estimatepriority <nblocks>
validateaddress <“anoncoinaddress”>
verifymessage <“address”> <“signature”> <“message”>
== Wallet ==
addmultisigaddress <nrequired> <[“key”,...]> [“account”]
backupwallet <“destination”>
dumpprivkey <“address”>
dumpwallet <“filename”>
encryptwallet <“passphrase”>
getaccount <“anoncoinaddress”>
getaccountaddress <“account”>
getaddressesbyaccount <“account”>
getbalance [“account”] [minconf] [includeWatchonly]
getnewaddress [“account”]
getrawchangeaddress
getreceivedbyaccount <“account”> [minconf]
getreceivedbyaddress <“address”> [minconf]
gettransaction <“txid”> [includeWatchonly]
getunconfirmedbalance
getwalletinfo
importaddress <address> [label] [rescan=true]
importprivkey <“privkey”> [“label”] [rescan]
importwallet <“filename”> 
keypoolrefill [newsize]
listaccounts [minconf] [includeWatchonly]
listaddressgroupings
listlockunspent
listreceivedbyaccount [minconf] [includeempty] [includeWatchonly]
listreceivedbyaddress [minconf] [includeEmpty] [includeWatchonly]
listsinceblock [“blockhash”] [target-confirmations] [includeWatchonly]
listtransactions [“account”] [count] [from] [includeWatchonly]
listunspent [minconf] [maxconf] [“address”,...] )
lockunspent <unlock> <[{“txid”:“txid”,“vout”:n},...]>
move <“fromaccount”> <“toaccount”> <amount> [minconf] [“comment”]
sendfrom <“fromaccount”> <“toanoncoinaddress”> <amount> [minconf] [“comment”] [“comment-to”]
sendmany <“fromaccount”> <{“address”:amount,...}> [minconf] [“comment”]
sendtoaddress <“anoncoinaddress”> <amount> [“comment”] [“comment-to”]
setaccount <“address”> <“account”>
settxfee <amount>
signmessage <“anoncoinaddress”> <“message”>
walletlock
walletpassphrase <“passphrase”> <timeout>
walletpassphrasechange <“oldpassphrase”> <“newpassphrase”>

{% endhighlight %}