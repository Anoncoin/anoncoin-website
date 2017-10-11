---
layout: page
title: How to check if an Anoncoin node is reachable
permalink: /How_to_check_if_an_Anoncoin_node_is_reachable/
---

To check if an Anoncoin i2p node is reachable, use the following command from the terminal:

`nc -z -v -X 5 -x 127.0.0.1:4446 7zbwzykhyjcmmessswamkxfyya7hioiy2oq7voaw27625qwruqia.b32.i2p 9377`

To check if a Tor onion node is reachable, use

`nc -z -v -X 5 -x 127.0.0.1:9050 kjwhbac5hwwdimq7.onion 9377`
