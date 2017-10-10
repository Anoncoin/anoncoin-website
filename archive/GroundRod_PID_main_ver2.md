---
layout: page
title: GroundRod PID main ver2
permalink: /GroundRod_PID_main_ver2/
---

Here we show the result of 11000+ blocks mining after the hardfork2 on block 585555 using the GroundRod PID Retarget Difficulty Algo featured in the new 0.9.6.12 version of Anoncoin.

<https://github.com/Anoncoin/anoncoin/blob/master/src/pow.cpp>

The PID settings used in mainet after hardfork-block 585555 on 9.6.12 were changed since the 9.6.11 version.

<code>

**`OLD`` ``parameters`**`                                   `**`New`` ``parameters`**
`#define PID_PROPORTIONALGAIN `“`1.7`”`               PID_PROPORTIONALGAIN `“`1.6`”
`#define PID_INTEGRATORTIME `“`172800`”`              PID_INTEGRATORTIME `“`129600`”
`#define PID_INTEGRATORGAIN `“`5`”`                   PID_INTEGRATORGAIN `“`8`”
`#define PID_DERIVATIVEGAIN `“`0`”`                   PID_DERIVATIVEGAIN `“`3`”
`#define TIPFILTERBLOCKS_DEFAULT `“`21`”`             TIPFILTERBLOCKS_DEFAULT `“`21`”
`#define USESHEADER_DEFAULT false                 USESHEADER_DEFAULT false`
`#define NMAXDIFFINCREASE `“`200`”`                   NMAXDIFFINCREASE `“`150`”
`#define NMAXDIFFDECREASE `“`170`”`                   NMAXDIFFDECREASE `“`130`”
`#define DMININTEGRATOR 170                       DMININTEGRATOR 176`
`#define DMAXINTEGRATOR 190                       DMAXINTEGRATOR 195`
`#define WEIGHTEDAVGTIPBLOCKS_UP 4                WEIGHTEDAVGTIPBLOCKS_UP 9`
`#define WEIGHTEDAVGTIPBLOCKS_DOWN 6              WEIGHTEDAVGTIPBLOCKS_DOWN 20`
`const int64_t nTargetSpacing = 180;              nTargetSpacing = 180;`

</code>

-   Blocktime

[<File:9612blocktime.png>](/File:9612blocktime.png "wikilink")

-   Average Blocktime

This is a simple mean above all blocks since block 585555. Here we also see the avg blocktime tending to 188 sec.

[<File:9612avgblocktime.png>](/File:9612avgblocktime.png "wikilink")

-   Integral term

The integral term over 36 hours (129600 sec) is doing oscillations when no block are found for a long time. This permit to keep block subsidy as near as possible to the 180 sec/block.

[<File:9612Intterm.png>](/File:9612Intterm.png "wikilink")

-   PIDOut

The PID output is much more stable than before. Except a spike when no block was found for 5 hours, all is good.

[<File:9612pidout.png>](/File:9612pidout.png "wikilink")

-   TipsAvg

TipsAvg is looking quite OK except when a very slow block happened the tips average remain high for as much as 21 blocks and this is followed by long period of oscillation of difficulty because of the integral term.

[<File:9612tipsavg.png>](/File:9612tipsavg.png "wikilink")

-   Space

Block spacing shows that there are no more very long blocks that anoncoin was plagued with for 2 years. This is thank to new PID parameters that makes it retarget slow enough for multipools to get out of the chain before the difficulty increase too much. Also most block are less than 30 minutes, this is thanks to our automatic difficulty reduction at 30 minutes without block found which makes the multipool jump back on anoncoin chain to mine the newly reduced difficulty block. For 5 hours there was no block at some point but this was compensated with quick blocks and then it went back to the normal pace thanks to the integral term oscillation.

[<File:9612space.png>](/File:9612space.png "wikilink")

-   Space zoom

[<File:9612space3600.png>](/File:9612space3600.png "wikilink")

-   Space more zoom

A zoom around 180 sec show the block space trend to around 188 sec on average.

[<File:9612space360.png>](/File:9612space360.png "wikilink")

-   Difficulty

[<File:9612diff.png>](/File:9612diff.png "wikilink")

-   Log of difficulty

A logarithm of difficulty shows the extent of variation of difficulty between the slow difficult block and the quick easy blocks. We can see than now there is less than one order of magnitude between the two extremes of difficulty vs two order spikes before with the old parameters. So the moderate retargetting of the difficulty with these particular proportional gain, maximum diff increase and decrease and the longer periods of 9 and 20 blocks for both moving averages are much better on mainet.

[<File:9612logofdiff.png>](/File:9612logofdiff.png "wikilink")

-   Difficulty chart

Difficulty chart with the two moving average (blue and red) delimiting the range of oscillation of the PID (green). Sometimes the diff is allowed to go below the 20 blocks moving average of difficulty down, this is to reduce quickly the difficulty as long as no block below 180 sec is found. When a less than 180 sec block is found the reduced difficulty go back to the 20 block moving average. The moving average up is less aggressive than with the old parameters due to less gain for the PID, a lower allowed range and more blocks for the average. This avoid huge spike of difficulty that makes the miners afraid.

[<File:9612difficultychart.png>](/File:9612difficultychart.png "wikilink")

**Conclusion**

The GroundRod Retarget PID was tuned for slower retargetting on a mainnet populated by multipools of high fluctuation of difficulty. The new tuning of the parameters of the PID with less aggressive variation of difficulty reduced the ratio between easiest and hardest difficulty block to less than 10 times maximum (often the range is only about a doubling of difficulty). The target block spacing is much better with 180-188 sec average and we have no more long interval without block (1 of 5 hours after 11000 blocks).