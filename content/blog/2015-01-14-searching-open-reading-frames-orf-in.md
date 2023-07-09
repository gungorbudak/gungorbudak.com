---
author: Güngör Budak
date: '2015-01-14T19:46:00.001+03:00'
slug: searching-open-reading-frames-orf-in
tags:
- python
- open reading frames
- orf
- tag
- dna
- sequence
- taa
- codon
- tga
title: Searching Open Reading Frames (ORF) in DNA sequences - ORF Finder
year: '2015'
---

Open reading frames (ORF) are regions on DNA which are translated into protein. They are in between start and stop codons and they are usually long.

The Python script below searches for ORFs in six frames and returns the longest one. It doesn't consider start codon as a delimiter and only splits the sequence by stop codons. So the ORF can start with any codon but ends with a stop codon (TAG, TGA, TAA). Six frames are the sequence itself and its reverse complement, and each has three frames obtained by shifting one nucleotide right twice.

There are also local and online tools that perform the same task. My suggestions are:

* <a href="http://www.ncbi.nlm.nih.gov/projects/gorf/orfig.cgi" target="_blank">NCBI ORF Finder</a> (Online)
* <a href="http://star.mit.edu/orf/" target="_blank">STAR: Orf by MIT</a> (Online / Local)

<script src="https://gist.github.com/gungorbudak/e330e115eba0d64d3d0c.js"></script>
