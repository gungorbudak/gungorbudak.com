---
author: Güngör Budak
date: '2013-08-02T08:30:00.000+03:00'
slug: scoring-edges-network-inference-hpn
tags:
- causal edge
- hpn-dream
- network inference
- dream challenge
- in silico
- scoring edges
title: Scoring Edges Network Inference HPN-DREAM Challenge
year: '2013'
---

Yesterday, I managed to infer a network for some part of *in silico* data from the challenge. Since the challenge also asks for scoring the edges in networks, I developed the script further and add a function for that.

edgeScorer function gets data object of average time points for each curve in intervention/no-intervention sets and scores each edge for each set of conditions. For this, first, it looks for the largest difference among the sets and set it as maxDifference and later, it stores differences divided by maxDifference in another data object. In this way, the edge with maximum difference is scored as 1 and the rest is scored relative to it.

I will use these scores for network inference. I will determine a threshold and the network printed will be consisting only of the edges with a score above the threshold.
