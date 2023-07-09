---
author: Güngör Budak
date: '2012-07-19T09:35:00.000+03:00'
slug: bir-megablast-ciktisi-icerigi-refseq
tags:
- gaps
- strand
- megablast output
- refseq
- score
- blast
- e value
- identity
- megablast
- fasta
title: Bir MegaBLAST Ciktisi Icerigi - RefSeq Veritabani
year: '2012'
---

Asagida, deneme FASTA dosyasini refseq_genomic veritabaninda arayarak elde ettigim dosyadan, bir hitin ayrintilarini goruyoruz.

```
>>>>refseq_genomic_complete3:
AC_000033_0310 Continuation (311 of 1357) of AC_000033 from base 31000001 (AC_000033
             Mus musculus strain mixed chromosome 11, alternate
             assembly Mm_Celera, whole genome shotgun sequence. 2/2012)
          Length = 110000

Score =  115 bits (58), Expect = 4e-22
Identities = 74/79 (93%), Gaps = 2/79 (2%)
Strand = Plus / Minus

Query: 1     ctctctctgtct-tctctctctctctgtctctctctctttctctctcttctctctctctc 59
             |||||||||||| ||| ||||||||| ||||||||||| |||||||||||||||||||||
Sbjct: 89773 ctctctctgtctgtctttctctctctctctctctctctctctctctcttctctctctctc 89714

                                
Query: 60    tttctctctgccctctctc 78
             ||||||||| |||||||||
Sbjct: 89713 tttctctct-ccctctctc 89696
```


Ayrintilarda, ilk olarak **\>>\>>** karakterleriyle hit ile ilgili baslik bilgisi veriyor. Bunda, kullanilan verutabani, ilgili organizme ve genin karsilastirildigi kromozomu ve dizileme bilgisi, tarihiyle birlikte veriliyor. Ayrica, uzunlugunu da gorebiliyoruz. Bu alani, organizmanin ismini elde etmek icin kullanabilirim, bunun disinda projem icin baska amacla kullanmayacagim.

Daha sonra ayri maddeler halinda score, expectation value, identities, gaps ve strand bilgileri sunuluyor.

Son olarak da aranan dizi ile veritabaninda karsilastirilan dizinin karsilastirma sonucu, acik olarak baz eslestirilmesi gosterilerek veriliyor. Burada "Query" aradigimiz gen dizisi, "Sbjct" ise veritabaninda karsilastirilan dizi.
