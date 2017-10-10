---
layout: page
title: Coin control
permalink: /Coin_control/
---

**Coin Control** is a feature for advanced users that allows manual control over coin selection.

Every time that you receive coins, a new unspent output is added to the wallet. These outputs (“coins”) are combined as necessary for outgoing payments. Normally, this selection process happens automatically and outside the control of the user. The normal mode of operation is to choose the best inputs and outputs to a transaction algorithmically, where the algorithm tries to minimize *dust outputs*, i.e. small amounts of coins that cost more to spend than they are worth.

With Coin Control, the user can select which unspent outputs to use as inputs to a transaction. It also makes it possible to control to which address the change will go. Exercising manual control over coin selection allows for a degree of privacy by controlling which coins are used together, and thus what a third party looking at the block chain will see.

By default, coin control is not enabled in the Anoncoin Client. To enable coin control, go to “Preferences” menu, click on “Display”, and then select “Display coin control features”.

[Category: Anoncoin](/Category:_Anoncoin "wikilink")