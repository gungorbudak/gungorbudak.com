---
author: Güngör Budak
date: '2012-07-16T04:54:00.000+03:00'
slug: megablast-aramasini-hizlandirma
tags:
- perl
- megablast
- fasta
title: MegaBLAST Aramasini Hizlandirma
year: '2012'
---

Son zamanlarda sadece farkli veritabanlarinda, MegaBLAST'i en cabuk ve etkili bir sekilde calistirmanin yolunu ariyorum ve FASTA dosyasi olusturma asamasinda, gercekten cokca ise yarayan bir yontem danismanim tarafindan geldi.

Daha once tum dizilerin bulundugu tek bir FASTA dosyasindan arama yapiyordum ve bu zaman kaybina yol aciyordu. Her ne kadar dosya bir sefer acilsa da her seferinde dosya icinde satirlara gidip onu okuman, zaman alan bir islem. Bunu, dosyadaki her okumayi, ayri bir FASTA dosyasi haline getirerek cozduk.

Su an elimizde 5.5 milyon ayri dosya olsa da, eskisine gore cok daha hizli arama yapabiliyoruz.

Buna gore MegaBLAST calistirma scriptim de asagidaki gibi degisti.

```perl
#!user/local/bin/perl

$database = $ARGV[0];
$dir = $ARGV[1]; #directory for sequences
$sp = $ARGV[2]; #starting point
$n = $ARGV[3] + $sp;

while (1) {
    system("megablast $dir/read_$sp.seq $database -OUTFILE=read_$sp.megablast -nofilter -nobatch -d");
    $sp++;
    last if ($sp == $n);
}
```
