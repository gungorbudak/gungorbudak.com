---
author: Güngör Budak
date: '2014-12-22T03:01:00.000+03:00'
slug: structural-superimposition-of-local
tags:
- pdb
- structural superimposition
- pairwise sequence alignment
- biopython
- biopdb
- rmsd
- local alignment
title: Structural Superimposition of Local Sequence Alignment using BioPython
year: '2014'
---

This task was given to me as a homework in one of my courses at the university and I wanted to share my solution as I saw there is no such entry on the Internet.

Objectives here are;

* Download (two) PDB files automatically from the server
* Do the pairwise alignment after getting their amino acid sequences
* Superimpose them and report RMSD

Bio.PDB module from BioPython works very well in this case. It's what I used in this solution.

<script src="https://gist.github.com/gungorbudak/2739bbe14fc9b5f6efe4.js"></script>
