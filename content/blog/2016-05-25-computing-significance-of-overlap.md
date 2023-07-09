---
author: Güngör Budak
date: '2016-05-25T13:31:00.000+03:00'
slug: computing-significance-of-overlap
tags:
- compute significance
- phyper
- transcripts
- hypergeometric distribution
- gene sets
- p-value
- genes
- proteins
- sets
- hypergeometric test
- r
- r programming
title: Computing Significance of Overlap between Two Sets using Hypergeometric Test
year: '2016'
---

There are many cases where we have two sets (e.g. under two different conditions) of things such as transcripts, genes or proteins and we want to compute the significance of the overlap between them. Hypergeometric test is very simple and widely used option for such cases.

I'll use the **phyper** function in R but you can use the same idea in SciPy (Python).

Let's say you have from 200 genes (A);

* 10 genes common or overlapping (set B ∩ set C)
* 25 genes in set B
* 50 genes in set C
* 135 genes not in set B or set C

[![Hypergeometric test](/public/images/hypergeometric-test.jpg)](/public/images/hypergeometric-test.jpg)

To compute the significance of overlap use;

```r
phyper(10, 50, 200 - 50, 25, lower.tail = FALSE)
[1] 0.0214406
```

So, if your threshold for p-value is 0.05 (or 5%), then you can say the overlap is significant.
