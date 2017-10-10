---
layout: page
title: GroundRod PID main ver1
permalink: /GroundRod_PID_main_ver1/
---

Here we show the result of 5000+ blocks mining after the hardfork on block 555555 using the GroundRod PID Retarget Difficulty Algo featured in the obsolete 0.9.6.11 version of Anoncoin.

EDIT2: those settings were changed in the 0.9.6.12 version of Anoncoin at block 585555 due to the not good retargeting of ver1. Result of 11000 blocks mined (585555-596555) on mainet after hardfork2 [GroundRod_PID_main_ver2](/GroundRod_PID_main_ver2 "wikilink")

------------------------------------------------------------------------

The PID settings used in mainet are the one from the 9.6.11 version after hardfork-block 555555.

<code>

1.  define PID_PROPORTIONALGAIN “1.7”
2.  define PID_INTEGRATORTIME “172800”
3.  define PID_INTEGRATORGAIN “5”
4.  define PID_DERIVATIVEGAIN “0”
5.  define TIPFILTERBLOCKS_DEFAULT “21”
6.  define USESHEADER_DEFAULT false
7.  define NMAXDIFFINCREASE “200”
8.  define NMAXDIFFDECREASE “170”
9.  define DMININTEGRATOR 170
10. define DMAXINTEGRATOR 190
11. define WEIGHTEDAVGTIPBLOCKS_UP 4
12. define WEIGHTEDAVGTIPBLOCKS_DOWN 6

const int64_t nTargetSpacing = 180; </code>

Here are the results so far...

It seems mining on mainet is characterized by about 10% constant hashrate and 90% multipool hashrate jumping on and off the chain. Mining quick blocks at low diff and increasing the diff until it is high enough for them to leave. The slowest block is then on hold for indefinite amount of time till the 10% constant hashrate find it, then the decrease of difficulty due to not having found a block for hours is accompanied by multipools jumping on the lower difficulty block, finding quickly many blocks while the difficulty drop and then increase to a high difficulty, which make multipools leave, repeating the cycle.

So in those very difficult mining conditions this is what we have so far at block 560555 using PID with the above settings.

-   Blocktime

Blocktime is too slow with around 214.6 sec instead of 180 sec, we can see when no block was found for a long time with almost vertical section and many quick blocks with almost horizontal section. The oblique parts with flatter slope are mostly due to the integral term requesting quick blocks for long times, to try to reduce the increased time toward the target of 180 sec.

[<File:Blocktime.png>](/File:Blocktime.png "wikilink")

-   Average Blocktime

This is a simple mean above all blocks since block 555149. Here we also see the avg blocktime tending to 210 sec.

[<File:Avg_blocktime.png>](/File:Avg_blocktime.png "wikilink")

-   Integral term

The integral term over 2 days (172800 sec) is almost always at the maximum which is equal to (190 - 180 = 10) \* 5 + 180 = 230.

[<File:Intterm.png>](/File:Intterm.png "wikilink")

-   PIDOut

The PID output sum is characterized by periods of stability like from 1400-2000 or 3800-4400 interspersed with chaotic periods were the PIDOut achieve very high values. It is evident the higher percentage of constant mining in the stable period is enough to not have very long space without any found blocks like when the multipools alone are mining, leading to very high PIDOut due to no blocks for hours. We conclude there is some amount of constant mining relative to multipool mining which is needed to achieve stability. If nobody is mining or at a very low hashrate the high difficulty blocks then nothing can really help unless an automatically decreasing difficulty which is in fact possible with the PID (parameter useheader=1) but disabled on mainet due to lack of time consensus between peers and subsequent possible attack vector.

[<File:Pidout2.png>](/File:Pidout2.png "wikilink")

-   TipsAvg

TipsAvg is looking quite OK but it hides information about very slow blocks followed by very quick blocks.

[<File:Tipsavg.png>](/File:Tipsavg.png "wikilink")

-   Space

Block spacing shows the very long blocks that anoncoin is subject to. This is no new to PID, very long blocks were also found with KGW due to the same multipools inconstant hashrate. The difference between KGW and PID is PID gives much less quick block than KGW which gave around 140 at a time.

[<File:Space.png>](/File:Space.png "wikilink")

-   Space zoom

[<File:Spacezoom.png>](/File:Spacezoom.png "wikilink")

A zoom on the space chart shows the very quick blocks following the very long blocks. This is of course due to conjugated effect of decrease of difficulty by the PID to remove the impact of the long block and increased hashrate due to multipools jumping onto the chain to get the easy difficulty blocks.

-   Log of difficulty

A logarithm of difficulty shows the extent of variation of difficulty between the slow difficult block and the quick easy blocks. We can see there is two order of magnitudes between those two extremes which is a lot. This is partly due to a too strong retargetting of the difficulty with these particular proportional gain, maximum diff increase and decrease and the too short periods of 4 and 6 blocks for both moving averages.

[<File:Difficultylog.png>](/File:Difficultylog.png "wikilink")

-   Difficulty chart

The difficulty chart shows 400 blocks using the old Kimoto Gravity Well retarget algo followed by about 5000 blocks using the new GroundRod PID.

It is very well seen on this chart that sometimes there is only multipools mining with no constant hashrate (p.ex. 749-1378) and other times there is a constant hashrate stabilizing the fluctuation (p.ex. 1378-2092). The same conclusion can be done which is Anoncoin need some fraction of constant mining to have a well behaving chain, but miners have more incentive to mine on multipools so it is not easy to get this constant hashrate.

[<File:Diff.png>](/File:Diff.png "wikilink")

**Conclusion**

The GroundRod Retarget PID was tuned for quick retargetting in case of high fluctuation of difficulty, but with the necessity to have at least ca one hundred blocks at each hashrate levels. Here the pattern of mining is more like mine 25 easy, let others mine one hard, mine 25 easy, let others mine one hard. Consequently I am in the process of tuning the parameters of the PID to have less aggressive variation of difficulty for then the ratio between easy and hard difficulty block will be less than one hundred as it is actually, limiting the impact of higher and lower difficulty and hopefully smoothing the block distribution. The community will be updated when I will be satisfied with the new parameters. CS