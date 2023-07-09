---
author: Güngör Budak
date: '2012-07-26T07:48:00.000+03:00'
slug: birden-fazla-dizi-dosyalarindan-megablast-calistirmak
tags:
- dizi
- while
- repeating sequences
- blast
- perl
- nofilter
- script
- blastplus
- megablast
- tekrar eden diziler
- fasta
title: Birden Fazla Dizi Dosyalarindan MegaBLAST'i Calistirmak
year: '2012'
---

Asagidaki scripti, pipeline'in MegaBLAST aramasini daha hizli yapabilmek icin dusundugumuz bir teknige uygun olabilmesi icin yazdim. Yaptigi sey, her okuma icin olusturulmus ve formatlanmis dizi dosyalarini kullanarak veritabanlarinda belirtilen baslangic noktasi ve okuma sayisi ile arama yapmak.

```perl
#!user/local/bin/perl

$database = $ARGV[0];
$dir = $ARGV[1]; #directory for sequences
$sp = $ARGV[2]; #starting point
$n = $ARGV[3] + $sp;

while (1) {
    system("blastplus -programname=megablast $dir/read_$sp.seq $database -OUTFILE=read_$sp.megablast -nobatch -d");
    $sp++;
    last if ($sp == $n);
}
```

Burada her sey gercekten cok basit bir programlama ile isliyor. Tek yapilan sonsuz bir dongu olusturup bu dongu icinde tek tek dizileri system komutuyla MegaBLAST aracini kullanarak aramak. Scripte arguman olarak veritabani ismi, baslangic noktasi ve okuma sayisi veriliyor. Sonsuz donguden de, istenen okumalar arandiktan sonra cikiliyor.

Ayrica yeni scriptte megablast aracini artik farkli sekilde calistiriyorum. Bu sadece paketin en guncel halini kullanabilmek amaciyla degistirildi. Bununla birlikte "-nofilter" secenegini de kaldirdim. Boylece tekrar eden dizilerden (CTCTCT....) kurtulmus oluyorum.
