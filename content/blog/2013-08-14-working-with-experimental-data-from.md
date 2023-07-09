---
author: Güngör Budak
date: '2013-08-14T05:48:00.001+03:00'
slug: working-with-experimental-data-from
tags:
- hpn-dream
- network inference
- breast cancer
- dream challenge
- in silico
- network
title: Working with Experimental Data from Network Inference Challenge
year: '2013'
---

As I almost finished with *in silico* data, I moved on to analyses of experimental data using the same script. But since the characteristics of data is somehow different, before inferring network, I need to modify the script to be able to read experimental data files.

These differences include missing data values for some conditions. This makes analyses difficult because I have to estimate a value for them and this will decrease the confidence score of edges.

I'm working with BT20 (breast cancer) cell line data for the beginning. It has 234 rows of conditions and some of them (zeroth time points) are duplicates. Zero time points do not have stimulus treatment so for now I will exclude them and start with 5 seconds which is the second time point. So I have 6 time points (5, 15, 30, 60, 120, 240).

Stimuli are FGF1, Insulin, EGF, IGF1, HGF, Serum, NRG1, PBS and inhibitors are AKT, AKT & MEK and FGFR1 & FGFR3. And there are 48 phosphoproteins in BT20 cell line data. These make 192 different conditions and time points and 9216 data values.

In R, I defined a fashion for the data and I'm checking the data if it follows the expected pattern. If not, I create an empty data value for that condition and time point. Later, I'll try to estimate values for them. Also, I realized for 240 seconds rows, data does not follow the expected pattern. So now, I have to fix this and start estimation.

After these estimations, I will have a complete dataset as in *in silico* part and will use the same scripts for plotting the graphs of expression profiles and inferring and scoring networks.
