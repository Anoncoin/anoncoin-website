---
title: Creating themes
permalink: /Creating_themes/
---

The GUI version of Anoncoin uses the industry-standard Qt toolkit for graphic elements. This allows us to format the screen layout once and have it appear similar on Windows, Mac, Linux, etc. It works a lot like Cascading Style Sheets (CSS). You can change the color and sometimes the shape of various graphic items like labels, combo boxes, and text. Only hardcoded styles set by the program cannot be changed - for example the red “(out of sync)” message.

Each style is in its own directory along with any graphics it uses. The themes sub-directory is under the configuration directory, which is where anoncoin.conf is stored and the stylesheet is always named “styles.qss”. As an example, the stylesheet for the “I2Pdarkish” theme is under *{configdir}/themes/I2Pdarkish/styles.qss*. The directory name is what will appear in the drop-down box under “Options-&gt;Display-&gt;Theme”.

Layout
------

The layout of each screen is defined in the \*.ui files of the source code, which can be found in src/qt/forms. Each is slightly different but all contain common Qt layout items. It is handy to look at these files when designing complicated styles that affect specific named elements. The layout is much like CSS's box model. For example, here is a diagram of how the Overview screen was laid out in a recent version. [<File:anoncoin_layout.png>](/File:anoncoin_layout.png "wikilink")

As an example, we can tell it the style sheet that we want all QLabels to be black except for the Immature balance which we want to be grey. This would be done by defining first the normal color for QLabels, and then the specific color for labelImmature:

`QLabel {`
`        color: black;`
`}`
`QLabel#labelImmature {`
`        color: grey;`
`}`

Like CSS, you can style different states of an element, e.g.

`QTextEdit {`
`        padding: 4px;`
`        background-color: transparent;`
`        color: $text-color;`
`        border: none;`
`}`
``
`QTextEdit:disabled {`
`        color: $disabled-text-color;`
`}`

Reusing Colors
--------------

With any stylesheet we often must specify the same color in many places. If we want to later tweak the color we would have to edit each of those places. A short-cut has been created for this in Anoncoin. At the beginning of the styles.qss file we can define a commented labeled section where we list variable names starting with “$” and the values they hold. For example, if we know we are going to be using brown and yellow a lot for gradient shading but the text will be black, we could set the file up like this.

`/** [VARS]`
`        $maintext    = #000`
`        $border_1    = #3f3f00`
`        $dark-grad   = #5f5f00`
`        $light-grad  = #ffff00`
`[/VARS] */`
``
`QLabel {`
`        color: $maintext;`
`}`
`QComboBox`
`{`
`        border: 1px solid $border_1;`
`        background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 $dark-grad, stop:1 $light-grad);`
`        color: $maintext;`
`        padding: 1px 18px 1px 13px;`
`}`

Including Graphics
------------------

There is one special substitution that is available in the style sheet for easily finding any special graphics files, such as arrows or icons. If you place these files in the same directory as the styles.qss you can refer to that directory as “_themesdir”:

`QComboBox::down-arrow:disabled {`
`        image: url(_themesdir/down-arrow-disabled.png);`
`}`

[Category: Anoncoin](/Category:_Anoncoin "wikilink") [Category:Guides](/Category:Guides "wikilink")