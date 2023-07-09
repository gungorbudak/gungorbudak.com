---
author: Güngör Budak
date: '2013-11-28T09:11:00.001+03:00'
slug: how-to-get-transcripts-also-exons
tags:
- intron
- ensembl api
- exon
- exon and intron boundaries
- transcript
- gene
- ensembl
- fasta
- github
title: How to Get Transcripts (also Exons & Introns) of a Gene using Ensembl API
year: '2013'
---

As a part of my project, I need to obtain exons and introns of certain genes. These genes are actually human genes that are determined for a specific reason that I will describe later when I explain my project. But for now, I want to share the way to obtain this information using (Perl) Ensembl API. Note that Ensembl has started a beautiful way (<a href="http://beta.rest.ensembl.org/documentation/user_guide" target="_blank">Ensembl REST API</a>) of getting data but it is beta and <a href="http://www.biostars.org/p/87095/#87129" target="_blank">it doesn't provide exons / introns information</a>. So we have to use Ensembl API.

If you haven't installed Ensembl API, visit <a href="{{ site.baseurl }}{% post_url 2013-11-12-install-ensembl-api-and-bioperl-161-on %}" target="_blank">my Ensembl (Perl) API installation post</a>.

To begin with, I want to share a tutorial set by Ensembl, which I used to learn the API. Tutorials are really useful so for more detailed information about the API, please visit <a href="http://www.ebi.ac.uk/training/online/course/ensembl-filmed-api-workshop" target="_blank">filmed API workshop</a>. Also, <a href="http://www.ensembl.org/info/docs/Doxygen/index.html" target="_blank">Doxygen Perl documentation</a> provides information about classes of the API.

First, let's create a registry to be able to use adaptors:

```perl
use Bio::EnsEMBL::Registry;
my $registry = "Bio::EnsEMBL::Registry";
$registry->load_registry_from_db(-host => 'ensembldb.ensembl.org', -user => 'anonymous');
```

Basically, in this API (specifically <a href="http://www.ensembl.org/info/docs/Doxygen/core-api/index.html" target="_blank">Ensembl core database API</a>) we have "adaptors" (of genes, transcripts, ...) and "objects" (of genes, transcripts, ...). Adaptors are used to retrieve objects from Ensembl database. So, if you want to get a gene (object) information, first you have to generate a gene adaptor. Then, using "fetch_by_stable_id" method passing an argument as Ensembl gene ID (e.g. <a href="http://www.ensembl.org/Homo_sapiens/Gene/Summary?g=ENSG00000198590;r=3:37427760-37476988" target="_blank">ENSG00000198590</a>) gene object is obtained.

```perl
my $gene_adaptor = $registry->get_adaptor('Homo sapiens', 'Core', 'Gene');
my $gene = $gene_adaptor->fetch_by_stable_id('ENSG00000198590');
```

This gene object, then will be used to get transcripts and each transcript will be used to get exons and introns. We don't have to generate more adaptors because when we obtain gene object, transcript adaptor is automatically generated. This is the same for exons (introns don't have an adaptor because they are not stored separately in Ensembl databases). So, to get transcripts, we need to use "get_all_Transcripts" method in gene object:

```perl
foreach my $transcript (@{ $gene->get_all_Transcripts }) {
}
```

In foreach loop above, exons and introns can be retrieved by "get_all_Exons" and "get_all_Introns" methods in transcript object. And of course, each exon / intron can be obtained by looping in the same way.

```perl
foreach my $exon (@{ $transcript->get_all_Exons }) {
}

foreach my $intron (@{ $transcript->get_all_Introns }) {
}
```


I suggest you check if you have a non-empty object for all because for some genes, Ensemble databases return null objects and if you try to use any method over them, you get errors. So do checks using an if clause:

```perl
if ($gene) {
    # get its transcripts
}

if ($exon) {
    # get its sequence
}
```

  
After you get each object there are other methods to obtain its ID, sequence, location, etc. Here I will give methods for ID and sequence retrieval but you can always refer to <a href="http://www.ensembl.org/info/docs/Doxygen/core-api/index.html" target="_blank">Doxygen Perl (core API) documentation</a> for more information.

So to print ID of genes, transcripts and exons (not introns because they don't have...), we need to use "stable_id" method in objects:

```perl
print $gene->stable_id;
print $exon->stable_id;
```

To print sequence of objects:

```perl
print $exon->seq->seq();
print $intron->seq();
```

Please note the small difference in printing intron sequences.

So that's all. The complete script that I use to get exons and introns of a gene in FASTA format is available <a href="https://github.com/gungorbudak/eiban-metubin/blob/master/eiSingleGet.pl" target="_blank">here in my GitHub repo</a>. You run the script by supplying gene ID as an argument:

```bash
gungor@gungor:~$ perl projects/eiban/eiSingleGet.pl ENSG00000198590
```
