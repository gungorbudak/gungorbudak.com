---
author: Güngör Budak
date: '2014-04-13T05:25:00.002+03:00'
slug: download-human-reference-genome-hg19
tags:
- download human reference
- grch37
- download human genome
- human
- hg19
- human reference genome
- ucsc
- wget
- uncompress gz
- fasta
title: Download Human Reference Genome (HG19 - GRCh37)
year: '2014'
---

Many variation calling tools and many other methods in bioinformatics require a reference genome as an input so may need to download human reference genome or sequences. There are several sources that freely and publicly provide the entire human genome and I'll describe how to download complete human genome from University of California, Santa Cruz (UCSC) webpage.

<a href="http://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/" target="_blank">Index to the gzip-compressed FASTA files of human chromosomes can be found here</a> at the UCSC webpage.

This is Feb 2009 human reference genome (GRCh37 - Genome Reference Consortium Human Reference 37). You can find more information about it in the page. Note that there are the chromosomes we know such as chr1, chrM (mitochondrial), chrX but also chr11_gl000202_random. These strange ones are scaffolds and patches that include the region that have not been fully understood and placed into an actual chromosome. They are safe to include them in your reference genome. Also, they are very small relative to the actual chromosome files.

The codes I'll present below will be valid for Terminal in Linux OS or MacOS. In Windows, you may use Cygwin that comes with below commands or you may setup a virtual machine and install a Linux distro (You'll love it).

**1. Download all (GZ) files - chromosomes**

Create a directory that will store the downloaded files:

```bash
$ mkdir ~/Downloads/hg19
```

Change directory to "hg19/":

```bash
$ cd ~/Downloads/hg19
```

Download all files under hg19 chromosomes:

```bash
$ wget --timestamping 'ftp://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/*'
```

Or to download individual files (replace * with the file name) - if you don't want all of them:

```bash
$ wget --timestamping 'ftp://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/chr1.fa.gz' -O chr1.fa.gz
```

**2. Uncompress each GZ file - chromosome in the directory**

Create a directory that will store the uncompressed files:

```bash
$ mkdir uncompressed
```

Uncompress each using following single line loop into directory "uncompressed/" in Terminal:

```bash
$ for a in *.gz; do gunzip -c $a &gt; uncompressed/`echo $a | sed s/.gz//`; done
```

**3. Merge all chromosomes (1, 2, 3, ..., X, Y) in one FASTA file**

Change directory to "uncompressed/"

```bash
$ cd uncompressed
```

Concatanate all FASTA files into one:

```bash
$ cat *.fa &gt; hg19_ref_genome.fa
```

Or only actual chromosomes without scaffolds and patches:

```bash
$ cat chr1.fa chr2.fa chr3.fa chr4.fa chr5.fa chr6.fa chr7.fa chr8.fa chr9.fa chr10.fa chr11.fa chr12.fa chr13.fa chr14.fa chr15.fa chr16.fa chr17.fa chr18.fa chr19.fa chr20.fa chr21.fa chr22.fa chrM.fa chrX.fa chrY.fa &gt; hg19_ref_genome.fa
```

So, in this way, you will find hg19_ref_genome.fa (around 3.2 GB - containing whole genome of human) file in your `~/Downloads/hg19/uncompressed` directory.
