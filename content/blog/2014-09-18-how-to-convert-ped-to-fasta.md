---
author: Güngör Budak
date: '2014-09-18T10:35:00.001+03:00'
slug: how-to-convert-ped-to-fasta
tags:
- ped2fasta
- plink
- ped
- fasta
title: How to Convert PED to FASTA
year: '2014'
---

You may need the conversion of PED files to FASTA format in your studies for further analyses. Use below script for this purpose.

<a href="https://github.com/gungorbudak/ped2fasta" target="_blank">PED to FASTA converter on GitHub</a>

Gets first 6 columns of each line as header line and the rest as the sequence replacing 0s with Ns and organizes it into a FASTA file.

Note 0s are for missing nucleotides defined by default in PLINK

How to run:

```bash
perl ped2fasta.pl "C:\path\to\PED_File"
```
