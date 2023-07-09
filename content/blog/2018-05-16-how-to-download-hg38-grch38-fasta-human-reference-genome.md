---
author: Güngör Budak
date: '2018-05-16T14:00:00+03:00'
slug: how-to-download-hg38-grch38-fasta-human-reference-genome
tags:
- hg38
- grch38
- human
- reference genome
- fasta
title: How to Download hg38/GRCh38 FASTA Human Reference Genome
year: '2018'
---

hg38/GRCh38 is the latest human reference genome as of today which was released December, 2013. There are multiple sources for downloading it and also it comes in different versions.

[![Human chromosomes](/public/images/human-chromosomes.png)](/public/images/human-chromosomes.png)

The most well-known databases to use for downloading the human reference genomes are UCSC Genome Browser, Ensembl and NCBI. The naming convention hg38 is used by UCSC Genome Browser, while Ensembl and NCBI use GRCh38 to refer to the latest human reference genome.

The easiest way to download the actual FASTA formatted whole/per chromosome human reference genomes is to use FTP download sections of the databases.

Download sections for hg38/GRCh38

- [UCSC Genome Browser](http://hgdownload.soe.ucsc.edu/downloads.html#human)
- [Ensembl](https://www.ensembl.org/info/data/ftp/index.html)
- [NCBI](https://www.ncbi.nlm.nih.gov/genome/51)

FTP Download sections for hg38/GRCh38 genomic/DNA sequences

- [UCSC Genome Browser](http://hgdownload.soe.ucsc.edu/goldenPath/hg38/bigZips/)
- [Ensembl](ftp://ftp.ensembl.org/pub/release-92/fasta/homo_sapiens/dna/)
- [NCBI](ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/001/405/GCF_000001405.38_GRCh38.p12/)

The above links should take you to the pages where you can find the resources for downloading human reference genome. You will realize that there are DNA, cDNA/RNA and protein versions of the human reference genome. These show the extend of the sequences based on the given version. For example, protein sequences are the parts of DNA sequences which are annotated to have protein products.

In these resources, you will also see that there are unmarked, soft-marked and hard-marked versions of the same version (i.e. genomic/DNA sequences). As indicated in the corresponding sections, the masking is done based on the algorithms for detecting regions that have repeats. In the case of hard-masking, the detected repeats are converted to N's, whereas the soft-marked ones have the repeats as lower-case letters.

To actually download them to your computer, just right-click and save the link or copy the link and use a command line tool such as `wget` to download it. For example, for UCSC Genome Browser's hg38 human reference sequence, the link:

```
wget http://hgdownload.soe.ucsc.edu/goldenPath/hg38/bigZips/hg38.fa.gz
```

To extract the FASTA file from the gzip archive, use a tool such as `7zip` on Windows or use `gunzip` tool on Linux/macOS:

```
gunzip hg38.fa.gz
```

[Heng Li posted several issues with the human reference genomes given in these resources](http://lh3.github.io/2017/11/13/which-human-reference-genome-to-use) and suggests the following compressed FASTA file to be used as hg38/GRCh38 human reference genome.

```
ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/001/405/GCA_000001405.15_GRCh38/seqs_for_alignment_pipelines.ucsc_ids/GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz
```
