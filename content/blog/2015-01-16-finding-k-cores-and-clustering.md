---
author: Güngör Budak
date: '2015-01-16T12:03:00.000+03:00'
slug: finding-k-cores-and-clustering
tags:
- cores
- networkx
- clustering coefficient
- python
- core_number
- k-core
- clustering
title: 'Finding k-cores and Clustering Coefficient Computation with NetworkX '
year: '2015'
---

Assume you have a large network and you want to find k-cores of each node and also you want to compute clustering coefficient for each one. Python package <a href="http://networkx.github.io/" target="_blank">NetworkX</a> comes with very nice methods for you to easily do these.

k-core is a maximal subgraph whose nodes are at least k degree [1]. To find k-cores:

Add all edges you have in your network in a NetworkX graph, and use <a href="http://networkx.github.io/documentation/networkx-1.9.1/reference/generated/networkx.algorithms.core.core_number.html" target="_blank">core_number</a> method that gets graph as the single input and returns node – k-core pairs.

```python
cores = networkx.core_number(G)
```

If you also need to compute clustering coefficient each node, use <a href="http://networkx.github.io/documentation/networkx-1.9.1/reference/generated/networkx.algorithms.cluster.clustering.html?highlight=clustering#networkx.algorithms.cluster.clustering" target="_blank">clustering</a> method which gets graph and node as inputs for unweighted and returns a floating number as the clustering coefficient of the node.

```python
cc = networkx.clustering(G, node)
```

Below there is an example script that does these operations. Read the code and prepare your input accordingly.

<script src="https://gist.github.com/gungorbudak/2f6e05b815e9d0479a31.js"></script>

**References**

1\. Preventing Unraveling in Social Networks: The Anchored k-Core Problem, <a href="http://www.cs.cornell.edu/home/kleinber/icalp12-kcore.pdf">http://www.cs.cornell.edu/home/kleinber/icalp12-kcore.pdf</a>
