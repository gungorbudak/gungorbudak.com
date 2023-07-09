---
author: Güngör Budak
date: '2018-08-07T10:00:00+03:00'
slug: convert-gene-symbols-to-entrez-ids-in-r
tags:
- id conversion
- gene symbol
- entrez id
- r
- r programming
title: Convert Gene Symbols to Entrez IDs in R
year: '2018'
---

Bioinformatics studies usually includes gene symbols as identifiers (IDs) as they are more recognizable comparing to other IDs such as Entrez IDs. However, certain analyses (tools) may not use gene symbols as there are usually more than one symbol so it is more difficult to implement a method to work with gene symbols. In such cases, you may need to do a conversion which is very common thing to do in bioinformatics.

For this task, I have been using `org.Hs.eg.db` Bioconductor package which have worked very well so far. It is a genome wide annotation for human, primarily based on mapping using Entrez Gene identifiers.

Open the R console or RStudio and go to its console and use following commands to install and load the package:

```r
# install
source('https://bioconductor.org/biocLite.R')
biocLite('org.Hs.eg.db')

# load
library('org.Hs.eg.db')
```

Run `columns(org.Hs.eg.db)` to see available identifiers that can be used in this package. There are actually a lot of things such as Ensembl IDs, Uniprot IDs, protein families and GO annotations:

```r
columns(org.Hs.eg.db)
 [1] "ACCNUM"       "ALIAS"        "ENSEMBL"      "ENSEMBLPROT" 
 [5] "ENSEMBLTRANS" "ENTREZID"     "ENZYME"       "EVIDENCE"    
 [9] "EVIDENCEALL"  "GENENAME"     "GO"           "GOALL"       
[13] "IPI"          "MAP"          "OMIM"         "ONTOLOGY"    
[17] "ONTOLOGYALL"  "PATH"         "PFAM"         "PMID"        
[21] "PROSITE"      "REFSEQ"       "SYMBOL"       "UCSCKG"      
[25] "UNIGENE"      "UNIPROT"   
```

Let's make a sample gene symbol list to work with and do the conversion using `mapIds` which required 4 arguments, the first is the object itself, the second is the list of identifiers (symbols in this case), the third is the identifier type we want to convert to, and the last is the type of identifier for the second argument:

```r
# you will have your own list here
symbols <- c('AHNAK', 'BOD1L1', 'HSPB1', 'SMARCA4', 'TRIM28')

# use mapIds method to obtain Entrez IDs
mapIds(org.Hs.eg.db, symbols, 'ENTREZID', 'SYMBOL')
'select()' returned 1:1 mapping between keys and columns
   AHNAK   BOD1L1    HSPB1  SMARCA4   TRIM28 
 "79026" "259282"   "3315"   "6597"  "10155"
```

As you see the function `mapIds` returned Entrez gene IDs for the given gene symbols.

You can assign the result to a variable and use it wherever you want.

Check out [org.Hs.eg.db reference manual](https://bioconductor.org/packages/release/data/annotation/manuals/org.Hs.eg.db/man/org.Hs.eg.db.pdf) for more information.
