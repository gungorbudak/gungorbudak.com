---
author: Güngör Budak
date: '2012-06-20T13:46:00.001+03:00'
slug: dizileme-calismalarini-kirleten
tags:
- pipeline
- viral dna
- bakteri
- perl
- genom dizileme
- virüs
- maya
- megablast
- dizileme
- dna
- eşleşmeyen okuma
- kirletici
- pipeline development
- pipeline geliştirme
- husar
- eşleşen okuma
title: Dizileme Çalışmalarını Kirleten Organizmaları Tespit Etme
year: '2012'
---

Bu yaz stajımda ilk olarak başlayacağım çalışma yavaş yavaş şekilleniyor. Bu çalışmada bir pipeline oluşturup, bunu laboratuvarlarda dizileme (sequencing) örneklerini kirleten organizmaları bulmaya çalışacağım.

Laboratuvarlarda birçok nedenden dolayı örnekler başka organizmalar ya da yabancı DNA tarafından kirlenebiliyor. Bunlar bakteri, maya olabilir ya da bir virüs DNA'sı da olabilir. Siz bir DNA'yı diziledikten sonra onun referansıyla eşleştirme çok az oranda çıkabiliyor. Bu da yabancı DNA'nın olabileceğini gösteriyor. Bir başka neden referans DNA'nın farklı olması da olabilir. Aynı zamanda algoritmada da hata olabilir. Bunlar düşük oranda eşleşme çıkaran sonuçların nedenleri olarak gösterilebilir.

Kirletici bir faktör olup olmadığını tespit etmenin çeşitli stratejileri var. Örneğin biri, genomu diziledikten ve referansıyla eşleştirdikten sonra, eşleşmeyen kısmını bu genomdan çıkarıp, onu olası tüm organizmalarla deneyerek, en fazla eşleşmeyi bulmaya çalışmak ve organizmayı belirlemek. Bunu Husar paketinde bulunan MegaBLAST ile yapabiliyoruz. Veri tabanında sahip olduğu 20.000 canlı DNA'sı üzerinden karşılaştırma yaparak, kirletici organizmaları listeleyebiliyor.

İşte yapacağım çalışmada, pipeline dizilenen genomu alacak, referansıyla eşleştirmeye çalışacak, eşleşmeyen kısmını çıkarıp bunu MegaBLAST ile diğer genomlarla karşılaştırıp bana olası organizmaların listesini döndürecek. Oldukça kolay görünen ancak verilerin çok çok büyük boyutlara sahip olması sebebiyle uzun zaman alacak bir çalışma.

Başlamadan önce Perl programlama diline ve MegaBLAST aracına alışmam gerekiyor. Elbette literatür araştırması yaparak, başka stratejiler geliştirilip geliştirilmediğini kontrol etmekte de fayda var.
