---
author: Güngör Budak
date: '2014-02-27T06:11:00.001+03:00'
slug: an-exon-of-length-2-appeared-in-ensembl
tags:
- databases
- ncbi
- transcripts
- introns
- exons
- genes
- eiban
- ensembl
title: An Exon of Length 2 Appeared in Ensembl
year: '2014'
---

I want to share an interesting finding about our research on exon/intron analysis of human evolutionary history.

So I had the genes that emerged at each pass point of human history and I was using Ensembl API to get exons and introns of these genes to perform further analyses.

There was one gene (<a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?db=core;g=ENSG00000197568;r=1:70820488-70851022" target="_blank">ENSG00000197568 - HERV-H LTR-associating 3 - HHLA3</a>) with a surprise. Because it's one transcript (ENST00000432224) had an exon (ENSE00001707577) of length 2. At first I couldn't realize the oddness but later in group discussions it was obvious that an exon with only 2 bases cannot occur.

So we checked different databases (NCBI, UCSC Genome Browser) for the same gene and realized that that exon was not there and their gene finding algorithms placed those 2 bases as a part of an intron and the transcript has one less exon compared to the one in Ensembl databases.

This shows gene finding algorithms are still not in their best forms and different sources need to be checked before going into a conclusion about exons/introns.
