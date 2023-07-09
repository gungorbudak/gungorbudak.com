---
author: Güngör Budak
date: '2012-08-03T05:15:00.002+03:00'
slug: dorduncu-deneme-veriseti-mus-musculus
tags:
- pipeline
- mus musculus
- insan genomu
- eşleşmeyen okuma
- bam
- bam2fastq
- ev faresi
- insan
- fastq
title: 'Dorduncu Deneme Veriseti: Mus Musculus Genomu'
year: '2012'
---

Simdiye kadar ilk uc veriseti de insan genomuna aitti. Pipeline'i bu genomlarla deneyip, yer yer iyilestirmeler yaptim. Simdi ise baska organizmalarla da deneyip, daha fazla sonuc alip bunlari inceleyecegim ve gene gerekli iyilestirmeleri yapacagim.

Bu ilk farkli veriseti fareden geliyor. *Mus Musculus* tur adina ve ev faresi olarak yaygin isme sahip bu organizma da model organizma olarak calismalarda kullanildigi icin dizisi daha siklikla cikarilan diger bir organizma.

Bi dizilemeyi yapan, birlikte calistigim laboratuvardan cesitli BAM formatinda dizi dosyalari aldim. Bunlardan birini `bam2fastq` araciyla FASTQ formatina cevirerek dorduncu analizime baslayacagim. Bu dosyada toplam 37994473 dizi var ve bunlarin 6440475 tanesi eslesmeyen diziler.
