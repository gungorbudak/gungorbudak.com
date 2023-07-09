---
author: Güngör Budak
date: '2014-09-19T07:14:00.001+03:00'
slug: data-preprocessing-ii-for-salmon-project
tags:
- time series
- signaling
- human
- salmonella
- modeling
- matrix
- reconstruction
title: Data Preprocessing II for Salmon Project
year: '2014'
---

So in our Multi-dimensional Modeling and Reconstruction of Signaling Networks in *Salmonella*-infected Human Cells project, we have several methods to construct the networks so the data is still needed to be preprocessed so that it can be ready to be analyzed with these methods.

One method needed to have a matrix first row as protein name and time series (2 min, 5 min, 10 min, 20 min), and the values of the proteins in each time series were to be 1 or 0 according to variance, significance and the size of fold change. So, if the variance was less than 15% and the significance was less than 0.05, the script collected values of peptides belonging to the same protein in all time series and all locations (N, M, C) and then got the maximum value from all and determined at which time the maximum value was observed. According to this, for each protein, "1" was put, under the time where it had maximum fold change among all time points and locations. And "0" was put for the rest of the times.

Proteins with variance NA, significance NA or fold change NA were ignored. And if there were multiple proteins for one row, there were split and each got the same 1 and 0s.

Yet another method needs to have such matrix but here values of the proteins can be multiple 1s because it requires all observed maximum values from all time points satisfying the conditions. Here, since the data is multi-dimensional (it has time series and locations), we need to decide how we arrange the data according to locations. For now, we haven't done it yet, so I'm going ro mention it later.

The script is written in Python and will be published soon.
