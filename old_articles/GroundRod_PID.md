---
layout: old_page
title: GroundRod PID
permalink: /GroundRod_PID/
---

Presentation of GroundRod PID
-----------------------------

EDIT2: those settings were changed in the 0.9.6.12 version of Anoncoin at block 585555 due to the not good retargeting of ver1 (see link EDIT1 below). Result of 11000 blocks mined (585555-596555) on mainet after hardfork2 [GroundRod_PID_main_ver2](/GroundRod_PID_main_ver2/ "wikilink")

EDIT1: Result (not good) on mainet after 5000 blocks mined (555555-556555) on mainet after hardfork1 [GroundRod_PID_main_ver1](/GroundRod_PID_main_ver1/ "wikilink")

------------------------------------------------------------------------

Here we show the results on testnet of using the GroundRod PID Retarget Difficulty Algo featured in the 0.9.6.11 version of Anoncoin.

<https://github.com/Anoncoin/anoncoin/blob/master/src/pow.cpp>

The PID settings used in this simulation are the one used for the 9.6.11 version ready for hardfork-block 555555.

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

**Timeline of the simulationː**

*`525000`*` Hardfork mainet with ASIC on a special build and reduce the diff around 20 times, keep it at this level for 2305 blocks`
*`527327`*` ASIC is switched on and off to reduce the difficulty by spacing the blocks till GPU level is reached. Difficulty go from 50000 to around 10`
*`530630`*` At this block the difficulty is 5.6 and GPU hashrate is increased 12 times`
*`531200`*` At this block the difficulty is 48.6 and GPU hashrate is decreased 12 times`
*`531800`*` At this block the difficulty is 14.8 and GPU hashrate is increased 12 times`
*`532280`*` At this block the difficulty is 68 and GPU hashrate is decreased 12 times`

### Block 525000 -&gt; 527307 ASIC difficulty drop 25 times at 350 MH/s scrypt

**Difficulty plot** from 1000000 to around 50000. The current difficulty is in green, the red average is the average used to cap the difficulty UP, the blue one is the average to cap the difficulty DOWN.

![Img](/img/Difflim_ASICdrop.png)

### Block 527327 -&gt; 532465

The **PIDOut** is the result of all three PID calculations ie the Proportional̟-Integral-Derivative terms summed

`dPidOutputTime = dProportionalTerm + dIntegratorTerm + dDerivativeTerm`
![Img](/img/Pidout.png)

The proportional gain value is one of the most important setting to get right, too little and the PID is not reactive enough, too high and it becomes wild in retargetting.

`dProportionalTerm = dProportionalGain * dSpacingError`

The value was set to `PID_PROPORTIONALGAIN `“`1.7`” for this particular nTargetSpacing of 180 sec (`const int64_t nTargetSpacing = 180`) and tipfilter of 21 (`TIPFILTERBLOCKS_DEFAULT `“`21`”).

Those three values are linked so changing the tipfilter or nTargetspacing will influence the proportional gain.

The derivative Term is defined by `dDerivativeTerm = dDerivativeGain * dRateOfChange`

in this particular PID setting, the Derivative term is set to `PID_DERIVATIVEGAIN `“`0`” so in fact anoncoin use a PI controller.

The PID integral term is calculated on the deviation from the `nTargetSpacing = 180`, the difference is multiplied by the integrator gain.

`dIntegratorTerm = (dIntegratorBlockTime - (double)nTargetSpacing) * dIntegratorGain + (double)nTargetSpacing;`

The integrator period is set to `PID_INTEGRATORTIME `“`172800`” so 48 h or 960 blocks.

The integral gain `PID_INTEGRATORGAIN `“`5`” is necessary to have the value settle quickly to the nTargetSpacing setpoint. The anti integral windup values `DMININTEGRATOR 170` and `DMAXINTEGRATOR 190` cap the integral term in case of huge change of block spacing (such as when lowering the diff so much as 5000 times like we just did). The differences between `DMININTEGRATOR 170` and `nTargetSpacing = 180` is multiplied by `dIntegratorGain 5` and so the minimum integral term is

`(170-180)*5 + 180 = -50 + 180 = 130`

Similarly the maximum integral gain is

`(190-180)*5 + 180 = 230`

The oscillation of the **integral term** due to the impact of the drop of hashrate of 5000 times are clearly seen in the following figure.
![Img](/img/Pid_intterm.png)

The **Tipsavg** is the median time of successive 21 blocks (`TIPFILTERBLOCKS_DEFAULT `“`21`”). It does not deviate too much of 180 sec per block even with those huge change in hashrate and the variation of individual blocks space.
![Img](/img/Pid_tipsavg.png)

The **Space** for individual blocks with moving average. Despite some blocks being very slow (due to drop in hashrate or variation in difficulty), the average is hovering around the `nTargetSpacing` of 180 sec.
![Img](/img/Pid_space.png)

A zoom on the **Space** averages. You can see than thanks to the integral term there are waves like fluctuation around the median time to recover from the slow blocks due to the drop of difficulty and variations due to the integral term feedback loop period of 48 hours. Compare with the integral term graphicː when integral term is the most elevated the block space is quickest and vice versa.
![Img](/img/Pid_spacezoom.png)

**Block time** is an easy way to see the linearity of the block spacing by plotting the time stamp for each block vs the block number. It shall be a straight line with a slope of `nTargetSpacing 180` if there was constant hashrate or perfect control.
![Img](/img/Pid_blocktime.png)

**Average blocktime** is another easy way to check the total block spacing by doing an average of each block spacing from begining to a certain point and plotting the result. The curve shall settle to 180 sec over time. It is the same thing than the integrator do but the integrator has a moving windows of 48 h while this curve average all the block space since the begining of the experiment.
![Img](/img/Pid_avg_blocktime.png)

This **Logarithmic scale of difficulty** per block show the overall change of difficulty since the initial drop of 50000 from ASIC level to a GPU level of 10, followed by the two GPU attacks at 12 times the hashrate.
![Img](/img/Pid_difficulty_log.png)

Finally the **Difficulty plot** for each block are given below. The current difficulty is in green, the red average is the average used to cap the difficulty UP, the blue one is the average to cap the difficulty DOWN.

First periodː dropping the diff 5000 times from ASIC (block 1 is 527327) to GPU level. Blocks 1-1050 are shown.
![Img](/img/Difflim1-1050.png)

The same period in logarithmic scale. Blocks 1-1050 are shown.
![Img](/img/Difflim1-1050log.png)

A constant hashrate period at low GPU level. There is some instability in the difficulty because it is still recovering from the huge drop in hashrate (integral term is still fluctuating widely). Blocks 1050-2100 are shown.
![Img](/img/Difflim1050-2100.png)

A constant hashrate period at low GPU level. The difficulty has stabilized now. You can see in no point the current difficulty in green touch the UP limit in red. The control is fully the PID and sometimes the limit average DOWN. Blocks 2100-3150 are shown. 
![Img](/img/Difflim2100-3150.png)

In the following period an attack of x12 times the hashrate was done. The limit average UP in red was quickly touched during the increase in hahsrate, limiting the difficulty the proportional gain of the PID was requesting. After the block slowed down the difficulty reached a plateau and the average UP was no more touched. On stopping the attack, the slow blocks diminished the difficulty which was first allowed to diminish twice to 0.588 (100/170, `NMAXDIFFDECREASE `“`170`”), then was allowed to even go lower than the limit average DOWN for a quicker difficulty decrease. Around block 750 the quick block made the difficulty go up toward the limit average DOWN. Blocks 3150-4200 are shown. ![Img](/img/Difflim3150-4200.png)

In this last period an attack of x12 times the hashrate was done. The attack was very powerful because there was a stream of lucky block that shoot the difficulty higher than needed, even with the limit average UP reached for several blocks. This show the necessity of the average because if there was none the difficulty would have shoot up even more up. For coins that are not as attacked by multipool as anoncoin the current settings of `PID_PROPORTIONALGAIN `“`1.7`” can be lowered or `NMAXDIFFINCREASE `“`200`” (the limit average UP) can be lowered or `WEIGHTEDAVGTIPBLOCKS_UP 4` (the number of blocks averaged for calculating the limit average UP) can be increased. By changing one of those three value (especially the limit average settings) something less responsive can be obtained to avoid overdrive of difficuly in case of such attack coiciding with lucky blocks.
![Img](/img/Difflim4200-5250.png)

If you have any question on the PID tuning feel free to mail cryptoslave@anoncoin.net