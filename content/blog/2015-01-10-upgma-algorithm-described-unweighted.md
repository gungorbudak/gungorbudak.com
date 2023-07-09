---
author: Güngör Budak
date: '2015-01-10T08:41:00.000+03:00'
slug: upgma-algorithm-described-unweighted
tags:
- upgma algorithm
- unweighted pair-group Method with arithmetic mean
- clustering algorithms
- molecular clock
- upgma
- ultrametric
- clustering
title: UPGMA Algorithm Described - Unweighted Pair-Group Method with Arithmetic Mean
year: '2015'
---

UPGMA is an agglomerative clustering algorithm that is <a href="http://lectures.molgen.mpg.de/Phylogeny/Ultrametric/" target="_blank">ultrametric</a> (assumes a molecular clock - all lineages are evolving at a constant rate) by <a href="http://lectures.molgen.mpg.de/Phylogeny/Ultrametric/" target="_blank">Sokal and Michener in 1958</a>.

The idea is to continue iteration until only one cluster is obtained and at each iteration, join two nearest clusters (which become a higher cluster). The distance between any two clusters are calculated by averaging distances between elements of each cluster.

To understand better, see <a href="http://www.southampton.ac.uk/~re1u06/teaching/upgma/" target="_blank">UPGMA worked example by Dr Richard Edwards</a>.
