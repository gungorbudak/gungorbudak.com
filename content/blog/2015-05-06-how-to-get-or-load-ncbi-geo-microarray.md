---
author: Güngör Budak
date: '2015-05-06T16:22:00.000+03:00'
slug: how-to-get-or-load-ncbi-geo-microarray
tags:
- gds
- geoquery
- microarray data
- ncbi
- load microarray data
- geo
- r
- r programming
- bioconductor
title: How to Get (or Load) NCBI GEO Microarray Data into R using GEOquery Package
  from Bioconductor
year: '2015'
---

R, especially with lots of Bioconductor packages, provides nice tools to load, manage and analyze microarray data. If you are trying to load NCBI GEO data into R, use <a href="https://github.com/seandavi/GEOquery" target="_blank">GEOquery package</a>. Here, I'll describe how to start with it and probably in my future posts I'll mention more.

**Installation**

```r
source("http://bioconductor.org/biocLite.R")
biocLite("GEOquery")
```
**Usage**

```r
library(GEOquery)
gds <- getGEO("GDS5072")
```

**or**

```r
library(GEOquery)
gds <- getGEO(filename="path/to/GDS5072.soft.gz")
```

`getGEO` function return a complex class type GDS object which contains the complete dataset. For example to obtain sample organism information:

```r
organism <- gds@header$sample_organism
print(organism)
[1] "Homo sapiens"
```

Obtain sample IDs:

```r
sample <- gds@dataTable@columns$sample
print(sample)
[1] GSM1095883 GSM1095886 GSM1095877 GSM1095878 GSM1095879 GSM1095880
[7] GSM1095881 GSM1095882 GSM1095884 GSM1095885 GSM1095876
11 Levels: GSM1095876 GSM1095877 GSM1095878 GSM1095879 ... GSM1095886
```

Obtain gene IDs:

```r
genes <- gds@dataTable@table$IDENTIFIER
head(genes)
[1] DDR1   RFC2   HSPA6  PAX8   GUCA1A UBA7
31596 Levels: ADAM32 AFG3L1P AK9 ALG10 ARMCX4 ATP6V1E2 ...
```

Obtain levels for the first sample:

```r
sample_1 <- gds@dataTable@table$GSM1095883
head(sample_1)
[1] "3362.6" "400"    "70.9"   "362.8"  "5"      "849"
```

GEOquery loads all parts of the data in a good format so that you can start your analysis directly. For more information visit <a href="https://github.com/seandavi/GEOquery/blob/master/vignettes/GEOquery.Rmd" target="_blank">package's GitHub vignettes</a>.
