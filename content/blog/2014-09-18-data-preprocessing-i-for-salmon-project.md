---
author: Güngör Budak
date: '2014-09-18T09:14:00.000+03:00'
slug: data-preprocessing-i-for-salmon-project
tags:
- david
- xls
- hgnc
- rstudio
- sublime text 2
- ipi
- salmonella
- modeling
- ms office 2013
- csv
- signaling
- uniprot
- reconstruction
title: Data Preprocessing I for Salmon Project
year: '2014'
---

Since we'll be using R for most of the analyses, we converted XLS data file to CSV using MS Office Excel 2013 and then we had to fix several lines using Sublime Text 2 because three colums in these lines were left unquoted which later created a problem reading in RStudio.

The data contains phosphorylation data of 8553 peptides. There are many missing data points for many peptides and since IPI IDs were used for peptides and these are not supported now, we had to convert IPI IDs to HGNC approved symbols although data had these symbols as names but they looked outdated.

To convert these IDs, first these IPI IDs were saved into a TXT files each in a new line. Then, <a href="http://david.abcc.ncifcrf.gov/conversion.jsp" target="_blank">conversion tool from Database for Annotation, Visualization and Integrated Discovery (DAVID)</a> was used to map IPI IDs to UniProt ACCs (57.125 lines of maps were obtained). Next, the obtained UniProt ACCs were used to map them to HGNC IDs using <a href="http://www.uniprot.org/uploadlists/" target="_blank">ID Mapping from UniProt</a> (10.925 lines of maps were obtained). Finally, to obtain HGNC approved symbols, <a href="http://www.genenames.org/cgi-bin/download" target="_blank">all protein coding gene data from HGNC</a> was downloaded with costumized colums allowing conversion of HGNC IDs to HGNC approved symbols (43.127 lines of maps were obtained). After collecting these three files, in R, the files were read and after column names were fixed, the union of these three files by UniProt ACC and HGNC ID was obtained (37.316 lines of maps were obtained). Later, we included these HGNC approved symbols in the data as a column to use them readily.

Later, I'll publish the R code I used for the conversion in a GitHub repo.
