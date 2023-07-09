---
author: Güngör Budak
date: '2015-01-16T20:06:00.000+03:00'
slug: network-clustering-with-neat-rnsc
tags:
- ilp
- pcsf
- cytoscape
- neat
- network clustering
- clustering
- rnsc
- network
- visualization
title: Network Clustering with NeAT - RNSC Algorithm
year: '2015'
---

As we have obtained proteins at different times points from the experimental data, then we have found intermediate nodes (from human interactome) using PCSF algorithm and finally with a special matrix from the network that PCSF created, we have validated the edges and also determined edge directions using <a href="http://ieeexplore.ieee.org/xpl/login.jsp?tp=&amp;arnumber=6560041&amp;url=http%3A%2F%2Fieeexplore.ieee.org%2Fiel7%2F8857%2F6679566%2F06560041.pdf%3Farnumber%3D6560041" target="_blank">an approach which a divide and conquer (ILP) approach for construction of large-scale signaling networks from PPI data</a>. The resulting network is a directed network and will be used and visualized for further analyses.

The first step was to cluster the network. <a href="http://rsat.ulb.ac.be/index_neat.html" target="_blank">RNSC (Restricted Neighbourhood Search Cluster Algorithm)</a> was used to cluster the network into 20 and these were imported to Cytoscape as a network table and the network is manually splitted into 20 clusters based on RNSC results on Cytoscape.

[![Salmonella network](/public/images/salmonella-network.png)](/public/images/salmonella-network.png)

Next, nodes in the network is colored based on time points when they are found to be significantly changed. In previously visualized network, some nodes seen at more than one time point were not shown correctly. In this one, if they are seen at more than one time point, they are colored with the corresponding colors of time points.

[![Salmonella network zoomed](/public/images/salmonella-network-zoomed.png)](/public/images/salmonella-network-zoomed.png)
