---
author: Güngör Budak
date: '2013-08-12T09:48:00.001+03:00'
slug: in-silico-network-inference-last
tags:
- data-derived network
- cytoscape
- hpn-dream
- network inference
- dream challenge
- in silico
- network
- visualization
title: In silico Network Inference Last Improvements and Visualization of Result in
  Cytoscape
year: '2013'
---

I'm almost done with the analysis of *in silico* data, although I need to decide if I need further analysis with the inhibiting parent nodes in the network. Last, I couldn't filter out duplicate edges, which were scored differently. Now, with some improvements in the script, low scores duplicates are filtered and there is a better final list of edges which is ready to be visualized.

I also tried visualizing it on <a href="http://www.cytoscape.org/" target="_blank">Cytoscape</a>. This is not required in the challenge but better to have to see the result. Below, there is a visualization of the result. It has colored edges and shaped edge ends (red and T-shaped edge is inhibiting, green and arrow-shaped edge is activating) according to type of interaction. Each edge has a score and it is indicated numerically and visually by having different thickness. The thicker the edge, the larger score it has relatively.

[![In silico network](/public/images/in-silico-network-cytoscape.png)](/public/images/in-silico-network-cytoscape.png)

*In silico* data-derived network from <a href="https://www.synapse.org/#!Synapse:syn1720047" target="_blank">HPN-DREAM Challenge</a>. *Click on the network to enlarge it.*

I will decide to do further analysis for *in silico* part according to the rank in the <a href="https://www.synapse.org/#!Wiki:syn1720047/ENTITY/56850" target="_blank">Leaderboard 1B</a>. I have already started modifying the script to read and process experimental data. I will define relations between inhibitors, stimuli and antibodies for experimental data as I did for *in silico* data, then infer the network using the same script as in *in silico* part.
