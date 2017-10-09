---
title: How to help Anoncoin translate
permalink: /How_to_help_Anoncoin_translate/
---

We are currently in the process of translating the Anoncoin client, and later will be translating the web page and wiki. To reach as many people as possible, we are in need of volunteers. Much of the initial translations has already been provided by the Bitcoin project. Nevertheless, we are in need of native speakers who can translate new material, most of which is related to our use of the i2p network.

How to translate
----------------

1.  Go to the [Transifex](https://www.transifex.com) website, click on login, and then create a new account.
2.  After verifying your account, choose the role of *translator*, click on *I want to join an existing project*, add the language that you can translate, and click *find project*.
3.  Click on the Anoncoin project. If the language that you want to translate is not there, then click *request language*.
4.  If the language you want to translate exists, click on it, click on *join team*, and then wait to be approved by the administrator.
5.  After approval, go to the [Anoncoin dashboard](https://www.transifex.com/organization/anoncoin-1/dashboard) and then click on the language you want to translate. Click the project *anoncoin*, choose the resource *qt-translation-v9*, and finally click *translate now* in the pop-up window. The rest should be obvious.

How to coordinate or review translations
----------------------------------------

If you would like to be the coordinator of a given language, or if you would like to review previously existing translations, please email either the language coordinator or one of the administrators.

Comments and hints
------------------

-   For strings like “(%1-bit)” or “127.0.0.1”, just copy the original text as the translated text.

<!-- -->

-   Please keep all formatting characters in the translated text, such as the ampersand in “&New”.

<!-- -->

-   Please place the ampersand in the same place as the original translation, usually before the word, or after the first character as in “C&hoose”.

<!-- -->

-   Do not translate strings that are hardcoded constants, such as “inbound.quantity”, “outbound.lengthVariance”.

If the language doesn't exist, an easy starting point is to use the translation from the Bitcoin project (it if exists). To do so:

1.  Go to [this link](https://www.transifex.com/projects/p/bitcoin/resource/tx/).
2.  Click on the language, and then *download for use*.
3.  Open the file in an editor and replace all instances of “Bitcoin” and “bitcoin” with “Anoncoin” and “anoncoin”.
4.  Go back to the [Anoncoin dashboard](https://www.transifex.com/organization/anoncoin-1/dashboard), click on the language to translate, the anoncoin project, and the resource *qt-translation-v9*, and then *upload file*.

[Category:Anoncoin](/Category:Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")