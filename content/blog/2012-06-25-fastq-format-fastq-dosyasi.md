---
author: Güngör Budak
date: '2012-06-25T11:01:00.000+03:00'
slug: fastq-format-fastq-dosyasi
tags:
- emacs
- dkfz
- gzip
- perl
- megablast
- header
- fastq
- bwa
- identifier
- husar
- unix
- fasta
title: FASTQ Formatı - FASTQ Dosyası
year: '2012'
---

Bugün programı oluştururken kullanacağım "test" dizilimini aldım. İki adet FASTQ dosyasından oluşuyor, her biri sıkıştırılmış ama buna rağmen boyutları 6 GB civarı. Ben elbette çok zaman kaybetmek istemediğim için bu dosyalardan birinin sadece bir kısmını kullanacağım.

Amacım, bu FASTQ dosyalarındaki eşleşebilen okumaları BWA aracı ile bularak, daha sonra onları çıkarmak. Ve kalan eşleşemeyen okumaları MegaBLAST aracının anlayabileceği bir dilde (FASTA formatında) kaydetmek.

Bu arada tüm projeyi bir Unix bilgisayarda hazırladığım için birçok komut öğreniyorum, daha sonra bunları ayrıca yazmaya çalışacağım. Örneğin sıkıştırılan bir dosyayı gzip -d dosya komutuyla çıkarıyorum, eğer özgün dosyayı korumak istiyorsam komuta -c ekliyorum.

Ayrıca Perl scriptlerini Emacs metin editöründe hazırlayacağım. Hiç alışkın olmadığım kısayollara ve özelliklere sahip olduğu için şimdilik zorlanıyorum. Tamamen öğrendikten sonra Emacs ile ilgili yazılar da yazmayı planlıyorum.

**FASTQ Formatı**

Bir FASTQ dosyasında her dizilim için (diyelim ki bir dizilim 151 bp) dört adet satır bulunuyor ve bu dört özel satır alt alta bu dosyada her dizilim için sıralanıyor. Bu satırların ilki başlık (header) ve dizilim ile ilgili özel belirteç (identifier) bulunuyor ve @ karakteri ile başlıyor. İkinci satır doğrudan baz dizilimini gösteriyor. Üçüncü satırda açıklamalar bulunuyor, boşsa sadece bir + karakteri görüyoruz. Son satır ise dizilimin kalitesini belirten kodlara sahip.
