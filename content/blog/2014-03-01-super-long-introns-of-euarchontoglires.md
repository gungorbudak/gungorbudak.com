---
author: Güngör Budak
date: '2014-03-01T13:55:00.000+03:00'
slug: super-long-introns-of-euarchontoglires
tags:
- intron length
- protein coding
- intron
- ensembl api
- human
- biotype
- exon
- exon and intron boundaries
- ensembl
- euarchontoglires
- homo sapiens
title: Super Long Introns of Euarchontoglires
year: '2014'
---

There was another weird result I got about my exon/intron boundaries analysis research. To less diverse species' genes, intron lengths are shown to increase. However, according to my findings, at a point of Euarchontoglires or Supraprimates, this increase is very sharp and seems unexpected. So, I looked at exon/intron length each gene in each taxonomic rank and try to see what makes Euarchontoglires genes with that long introns.

[![Exon - intron lengths 1](/public/images/exon-intron-lengths-1.png)](/public/images/exon-intron-lengths-1.png)

As you see in the graph above, Euarchontoglires introns are very long compared to the rest. So I got the Euarchontoglires genes having more than 10000 bp long introns in average which are;

<a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?db=core;g=ENSG00000176124;r=13:50656307-51297372;t=ENST00000378180" target="_blank">ENSG00000176124</a> (61886 bp)
<a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?g=ENSG00000255470;r=11:18161733-18211042;t=ENST00000527671" target="_blank">ENSG00000255470</a> (48283 bp)
<a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?g=ENSG00000233611;r=2:237076090-237203570" target="_blank">ENSG00000233611</a> (43231 bp)</div><div><a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?g=ENSG00000253161;r=8:37278859-37411701" target="_blank">ENSG00000253161</a> (23128 bp)<a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?g=ENSG00000056487;r=22:45277042-45405880" target="_blank">ENSG00000056487</a> (13482 bp)

When I checked their summaries on Ensembl, I saw that most of them have transcripts that are not protein coding so they tend to have longer introns relative to protein coding transcripts' introns.

So a solution might be retrieving biotypes of transcripts and filtering the ones that are not protein coding. Because in this project, we're focusing on the protein coding genes.

<a href="http://biyoenformatik.blogspot.com.tr/2013/11/how-to-get-transcripts-also-exons.html" target="_blank">Remember Ensembl API</a>, getting biotypes is really easy. All I need to do is add following to my script;

```perl
$transcript_object->biotype
```

So I got my data with its biotype information and filtered out the ones that are not protein coding. Later, when I repeated the analysis with the new data, the unexpected peak at Euarchontoglires introns was gone.

[![Exon - intron lengths 2](/public/images/exon-intron-lengths-2.png)](/public/images/exon-intron-lengths-2.png)

There is still a lot to be done of course, but for this particular issue, I solved it in this way.
