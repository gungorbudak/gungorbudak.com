---
author: Güngör Budak
date: '2013-08-01T09:42:00.000+03:00'
slug: determining-edges-more-progress-on
tags:
- midas
- causal edge
- sif
- antibody
- excitatory
- network inference
- inhibitory
- dream challenge
- in silico
title: Determining Edges More Progress on Network Inference
year: '2013'
---

Lately, I have been writing an R script to infer network using *in silico* data. Last version of the script was reading MIDAS file and plotting expression profiles. I have modified it and now it reads MIDAS file, does some analyses and prints causal relations to a file. This file is a SIF file as required.

This dataset is generated with 20 antibodies but only 3 of them are perturbed. Also, for one, stimulus is missing. So, right now I can only determine causal edges between 2 of them and the rest.

In script, midasReader functions gets the content and stores each experiment in data object. And dataOptimizer reads the data object and makes it ready for inference. It does some kind of curve comparison (the curves obtained using dataPlotter, for example) and stores the results in another data object. Finally, networkInferrer gets this data object and compares related experiments and decides which kind of edge and prints in into a SIF file.

dataOptimizer does its job by taking average of all time points that belong to the same kind of experiment (the same stimulus and/or inhibitor set). Decision will be made by comparing the average of values obtained by intervention and the ones by no-intervention.

networkInferrer compares intervention and no-intervention averages and sets "relation" variable accordingly. If intervention average value is smaller than no-intervention average value, then the "relation" variable is set to "1", because inhibition of parent node causes a decrease in the amount of child node, so the conclusion is that there is an excitatory (1) relationship between parent node and child node.

[![AB1 in silico network](/public/images/ab1-in-silico-network.png)](/public/images/ab1-in-silico-network.png)

The image above shows an example for two different sets. First, inhibition of AB12 with INH1 and stimulation with low amount of LIG1. Second, there is a change in the amount of stimulus. Both resulted the same kind of relation that is excitatory (1). Notice that these relations are defined between AB1 and AB12 because INH1 and LIG1 target AB12.

The same kind of inference can be done for AB5 which is the other antibody targeted by an inhibitor and stimulus. But since there is only inhibitor for AB8, I don't know how to analyze it yet.

In this approach, I can only look for relations between these 3 antibodies and the rest. But, since inhibition of a child node might cause something on another grandchild node, with this kind of subsequent analysis, relations for all antibodies can be determined with each other.
