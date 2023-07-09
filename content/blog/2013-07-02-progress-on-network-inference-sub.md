---
author: Güngör Budak
date: '2013-07-02T10:13:00.001+03:00'
slug: progress-on-network-inference-sub
tags:
- sif
- cellnoptr
- eda
- kegg
- bioconductor
- wikipathways
- microarray
- pkn
- network inference
- cnorfeeder
- dream challenge
- in silico
title: Progress on Network Inference Sub-Challenge
year: '2013'
---

This sub-challenge has several requirements:

- Directed and causal edges on the models (32 models - 4 cell lines × 8 stimuli)
- Edges should be scored (normalizing to range between 0 and 1) that will show confidence
- Nodes will be phosphoproteins from the data
- Prior knowledge network (that can be constructed using pathway databases) is allowed to be used (actually this is a must for some network inference tools)

First thing was to look for existing tools. ddepn seemed a good option but <a href="http://biyoenformatik.blogspot.nl/2013/06/network-inference-dream-breast-cancer.html" target="_blank">it didn't work for us</a>. We checked for <a href="http://www.bioconductor.org/packages/release/BiocViews.html#___NetworkInference" target="_blank">different tools on Bioconductor</a> for our purpose. There was a tool called CellOptNR, which I thought we could use it for the second sub-challenge. Actually, on Synapse, the second sub-challenge has been modified recently, so right now I'm sure about it. But for the first sub-challenge, CellOptNR and a tool related to it called <a href="http://www.bioconductor.org/packages/release/bioc/html/CNORfeeder.html" target="_blank">CNORfeeder</a> will be useful.

This tool gets two input. One is data from microarray experiments, which is simply protein abundance measurements under several stimuli/inhibitors and the other is a prior knowledge network (PKN) that can be constructed using different pathway sources such as <a href="http://wikipathways.org/" target="_blank">WikiPathways</a>, <a href="http://www.genome.jp/kegg/pathway.html" target="_blank">KEGG</a>. It uses various inference methods to integrate the data and validate the network models.

So, we need to construct a PKN with the phosphoproteins in the data and then infer the network models. Next, we need to score each edge on the models and store the results in SIF and EDA files.

This sub-challenge also has *in silico* data part where there are similar requirements.

I tried an example (from DREAM 4 Challenge) given in <a href="http://www.bioconductor.org/packages/release/bioc/vignettes/CNORfeeder/inst/doc/CNORfeeder-vignette.pdf" target="_blank">vignette of CNORfeeder</a> and it worked as expected. In vignette, a data-drive network is shown without an integration with any PKN but how it is created is not given.
