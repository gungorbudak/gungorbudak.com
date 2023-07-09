---
author: Güngör Budak
date: '2013-08-08T07:49:00.003+03:00'
slug: latest-progress-on-network-inference
tags:
- integration
- area under curve
- causal edge
- hpn-dream
- network inference
- dream challenge
- scoring edges
title: Latest Progress on Network Inference and Edge Scoring
year: '2013'
---

I have improved network inference part of the script slightly by changing the way of comparing intervention (presence of inhibitor and stimulus) and no intervention (presence of stimulus) data from *in silico* part.

Now, I'm using a function (simp) from an R package called <a href="http://cran.r-project.org/package=StreamMetabolism" target="_blank">StreamMetabolism</a>, which gets time points and data values and (does integration) calculates the area under the curve (Sefick, 2009). I do this integration for both condition and then I compare them.

I also set a threshold for edge scoring. First, I set it as 0.05 and looked at the graphs of low scores. The curves from the graphs were not significantly different for these low scores. So I made it 0.1 and again observed low scores. In this case, the curves were looking different enough to be compared and to be included as an edge in the networks.

I'm inferring the network in this part for these conditions:

|Inhibitors|Stimuli|Targets|
|----------|-------|-------|
|INH1_loLIG1|loLIG1|AB12_L1|
|INH1_hiLIG1|hiLIG1|AB12_H1|
|INH2_loLIG2|loLIG2|AB5_L2|
|INH2_hiLIG2|loLIG2|AB5_H2|
|INH3_loLIG1|loLIG1|AB8_L1|
|INH3_hiLIG1|hiLIG1|AB8_H1|
|INH3_loLIG2|loLIG2|AB8_L2|
|INH3_hiLIG2|hiLIG2|AB8_H2|

So each condition is scored separately but in networks characters like "L1" are stripped and only target names are written with the antibodies. Because of this, in networks I can get multiple results for the same kind of edge. Of course, they differ in score and I will only write the result with highest score.

Below, you can see the output from latest script.

[![Network edge scores](/public/images/network-edge-scores.png)](/public/images/network-edge-scores.png)

Somehow, I need to find more edges with considering targets (AB12, AB5 and AB8) as inhibitors or stimuli. For example, according to the output above, AB8 causes an inhibition in AB2. So the new analysis should be done using AB8 as inhibitor and stimuli for AB8 as stimuli for AB2. This will give another set of results of relations between AB8 and the rest. In this way, there can be some more subsequent analysis to obtain enough edge to construct a complete network.

**Reference**

Sefick, Stephen. 2009. *Stream Metabolism-A package for calculating single station metabolism from diurnal Oxygen curves.* From <a href="http://cran.r-project.org/package=StreamMetabolism">http://CRAN.R-project.org/package=StreamMetabolism</a>
