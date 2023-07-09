---
author: Güngör Budak
date: '2012-07-26T08:32:00.000+03:00'
slug: yeni-veri-setinin-incelenmesi
tags:
- pipeline
- perl
- bam
- script
- fastq
title: Yeni Verisetinin Incelenmesi
year: '2012'
---

Pipeline'i tasarlama asamasinda deneme amacli kullandigim onceki verinin cok kotu olmasi sebebiyle yeni bir veriseti aldim. Elbette deneme asamasinda birden fazla, farkli karakterlerde verisetleri kullanmak yararlidir. Ancak onceki veriseti anlamli birkac sonuc veremeyecek kadar kotuydu diyebilirim. Ayrintilarina [buradan]({% post_url 2012-07-06-eslestirme-ve-eslesmeyen-okumalari %}) gozatabilirsiniz.

Yeni veriseti, gene bir insan genomu verisi ve BAM dosyasinin boyutu 1.8 GB ve icinde eslenebilen ve eslenemeyen okumalari bulunduruyordu. Ben bam2fastq araciyla hem bu BAM dosyasini FASTQ dosyasina cevirirken hem de eslenebilen okumalardan ayiklayarak 0.2 GB'lik FASTQ dosyasi olusturdum. BAM dosyasinda 26759102 adet okuma (dizi) bulunuyordu ve ayiklamadan sonra 735741 adet eslenemeyen okuma FASTQ dosyasina yazildi. Bu, tum dizinin % 2.7'sinin eslenemedigini gosteriyor ki oldukca normal bir durum.

Bu yeni veriseti ile birlikte scriptleri degistirmeye devam ediyorum. Ozellikle inceleme yapmak icin kullandigim scriptte bircok degisiklik yaptim. Bunu daha sonra yazacagim.
