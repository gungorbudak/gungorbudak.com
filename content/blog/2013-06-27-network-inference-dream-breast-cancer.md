---
author: Güngör Budak
date: '2013-06-27T08:09:00.000+03:00'
slug: network-inference-dream-breast-cancer
tags:
- rppanalyzer
- ddepn
- cran
- sif
- rppa
- cellnoptr
- eda
- network inference
- r package
- r
- r programming
- dream challenge
title: Network Inference DREAM Breast Cancer Challenge
year: '2013'
---

The inference of causal edges are described as the change on a node seen after the intervention of another node. If the curves obtained over time overlap (under intervention or no intervention), then there is no relation. Otherwise, we can draw an edge between those nodes and according to the level, up or down, the edge will be activating or inhibiting. These causal edges are context-specific so in different cell line data, we may have different relations.

Also, edge confidence scores should be obtained. Right now, I have no idea how to get them but we will discuss.

The relations and scores will be stored in SIF and EDA files and submitted to the competition.

This can be done by writing scripts specific to the task. However, before that I have looked for existing tools. I have found some. There is an R package called RPPAnalyzer which is designed to read RPPA result and compare the samples and plot a graph at the end but this is not exactly what we need in this challenge (See <a href="http://cran.r-project.org/web/packages/RPPanalyzer/index.html" target="_blank">its CRAN page</a>). Another R package specifically written for constructing signaling networks is present, and it is called ddepn (Dynamic Deterministic Effects Propagation Networks). It infers signalling networks for time-course RPPA data (See <a href="http://ddepn.r-forge.r-project.org/" target="_blank">its R-Forge page</a>).

So I started with ddepn. I installed the package (R version 3.0.1). And before using our data, I used the example described in its vignette. A similar example is also present in <a href="http://cran.r-project.org/web/packages/ddepn/ddepn.pdf" target="_blank">its documentation</a>. However, I got an error before plotting the network. When I attempted to run ddepn function to apply genetic algorithm, it gives  "Error in get("envDDEPN") : object 'envDDEPN' not found". So I have to find a way to solve it, then I can move on doing the same for our data.

It looks like the inference I got from this step will be necessary for the next step with the data files. Because for the next step the use of CellNOptR package (See <a href="http://www.cellnopt.org/" target="_blank">its official page</a>) is suggested and it needs noth network and data to make predictions.
