---
author: Güngör Budak
date: '2013-06-27T07:51:00.000+03:00'
slug: dream-breast-cancer-sub-challenges
tags:
- time-course prediction
- network inference
- breast cancer
- dream challenge
- dmso
- visualization
title: DREAM Breast Cancer Sub-challenges
year: '2013'
---

I have been going over the sub-challenges before attempting to solve them. As I mentioned, there are three sub-challenges and somehow they are connected.

First, using given data and other possible data sources such as pathway databases, the causal signaling network of the phosphoproteins. There are 4 cell lines and 8 stimulus so they make total 32 networks at the end. Nodes are phosphoproteins and edges should be directed and causal (activator or inhibitor).

4 different treatments are applied to samples before stimulation, these are inhibition treatments and one of them is vehicle control (DMSO). After that, the samples are stimulated and their levels are measured in different time points.

This sub-challenge has also another part where *in silico* data is provided and only one network inference using the data is asked. The characteristics of this data is different. The training dataset has time points for 20 phosphoproteins under various stimuli and inhibition of nodes (See <a href="https://www.synapse.org/#!Wiki:syn1720047/ENTITY/56213" target="_blank">Sub-challenge 1: Network Inference</a> for more).

Second, predictions on phosphoprotein trajectories should be made. Also, it's asked to propose a model that can cover beyond of this data (breast cancer proteomics and *in silico* datasets) (See <a href="https://www.synapse.org/#!Wiki:syn1720047/ENTITY/56216" target="_blank">Sub-challenge 2: Time-course Prediction</a> for more).

Third, visualization of the data should be made to be interpreted in meaningful ways. This is only for breast cancer proteomics dataset (See <a href="https://www.synapse.org/#!Wiki:syn1720047/ENTITY/56221" target="_blank">Sub-challenge 3: Visualization</a> for more).
