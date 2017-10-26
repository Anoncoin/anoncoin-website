---
layout: page
title: Anoncoin address
permalink: /Sample_anoncoin.conf/
---

An **[Anoncoin](/About_Anoncoin) address** is an identifier of 27-34 alphanumeric characters, beginning with the letter **A**, that represents a possible destination for an anoncoin payment. Addresses can be generated at no cost by any user, and the user can have as many addresses as desired. An example of an Anoncoin address is [Acoin7tkEib9d8BfomQYUK66z5fhwN3DgV](/Donate).

An Anoncoin address is like an e-mail address
---------------------------------------------

Like e-mail, you can send anoncoins to a person by sending anoncoins to one of their addresses. For increased privacy, a person can have many different addresses. To simply accounting, a different address can be used for each type of transaction.

Addresses can be created offline
--------------------------------

Creating addresses can be done without an internet connection and does not require any contact or registration with the anoncoin network. The network starts tracking an address when it is first seen in a valid payment transaction.

It is possible to create large batches of addresses offline using freely available software tools. Generating batches of addresses is useful in several scenarios, such as e-commerce websites where a unique pre-generated address is dispensed to each customer.

An average desktop computer can generate thousands of new addresses per minute. Addresses are created simply by generating random numbers and then performing mathematical operations to derive matching pairs of “public” and “private” keys. Because addresses can be created easily and at minimal cost, it is not uncommon to create temporary addresses that can be discarded if unused.

Addresses are case sensitive and exact
--------------------------------------

Anoncoin addresses are case-sensitive. Addresses should be copied and pasted using the computer's clipboard wherever possible. If you hand-key an address, and each character is not transcribed exactly - including capitalization - the incorrect address will most likely be rejected by the software. The probability that a mistyped address is accepted as being valid is 1 in 2<sup>32</sup>, that is, approximately 1 in 4.29 billion.

Addresses have a “private key”
------------------------------

For most properly-generated addresses, there is at least one secret number known as a private key which is required for access to the funds assigned to that address.

When using the Anoncoin client, private keys are typically stored in the wallet file. For security (see [Securing your wallet](/Securing_your_wallet)), the wallet should be encrypted. The private key has a special purpose - it is mathematically needed to create valid transactions that spend the funds originally sent to the address. If the private key to an address is lost (for example, in a hard drive crash, fire or other natural disaster), any associated coins are effectively lost forever.

What's in an address
--------------------

Most anoncoin addresses are 34 characters long. They consist of random digits and uppercase and lowercase letters, with the exception that the uppercase letter “O”, uppercase letter “I”, lowercase letter “l”, and the number “0” are never used to prevent visual ambiguity. Some addresses can be shorter than 34 characters (as few as 27 in theory) and still be valid. A significant percentage of addresses are only 33 characters, and some addresses may be even shorter.

Several of the characters inside an Anoncoin address are used as a checksum so that typographical errors can be automatically found and rejected. The checksum also allows the software to confirm that a 33-character (or shorter) address is in fact valid and isn't simply an address with a missing character.

See also
--------

-   [Anoncoin](/About_Anoncoin)
-   [How to generate an Anoncoin vanity address](/How_to_generate_an_Anoncoin_vanity_address)
