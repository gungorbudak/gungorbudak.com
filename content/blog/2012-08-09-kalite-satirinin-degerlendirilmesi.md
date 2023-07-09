---
author: Güngör Budak
date: '2012-08-09T08:48:00.001+03:00'
slug: kalite-satirinin-degerlendirilmesi
tags:
- pipeline
- quality filter
- fastqc
- filter
- perl
- quality
- megablast
- prinseq
- fastq
- fastx toolkit
- fastq quality filter
- kalite
title: Kalite Satirinin Degerlendirilmesi - Quality Filter
year: '2012'
---

Kirleten organizma (konaminant) analizi yapacak olan pipeline'i daha fazla gelistirmek, daha anlamli sonuclar elde etmek icin ilk adimlara (henuz fastq dosyasini isliyorken) kalite filtresi eklemeyi dusunduk. Boylece belirli bir esik degerinden dusuk okumalari daha o asamadan filtreleyerek daha guvenilir sonuclar elde elebilecegiz.

Bu kalite kontrolunu fastq dosyasinda her okumanin 4. satirini anlayarak yapacagiz. Bu 4. satir (aslinda okumanin dizileme kalite skoru), cesitli dizileme cihazlari tarafindan cesitli sekillerde yaziliyor (kodlaniyor) ve bu kodlamadan tekrar kalite skorunu elde ederek filtreleme uygulanmasi gerekiyor. Bu yuzden oncelikle dizilme yapan cihazin kodlama (encoding) formatini bilmek ve bu skoru tekrar elde etmek gerekiyor. Henuz bu konuda bir fikrim yok. Dizileri aldigim bolume bir e-posta attim ve yakinda cihaz ile ilgili tum bilgileri edinecegim.

Bunu kendim de yapabilirim ancak yerine bir arac kullanmayi dusunuyorum. Simdilik bu araclar FASTX Toolkit icinde bulunan FASTQ Quality Filter araci, PRINSEQ ve FASTQC. Bu araclari tek tek arastirip hangisinin daha uygun oldugunu belirleyip onu pipeline'da kullanacagim.

Bu araclar temel olarak elimdeki fastq dosyasindan kalitesi dusuk okumalari cikarip atacak. Yani herhangi bir kesme yapmayacak, tamamen o okumayi siliyor olacak. Boylece elimde daha az ama guvenilir okuma kalacak.

Daha sonra bu okumalar arasindan megablast aramasi icin kullanilacaklari rastgele secmeyi dusunuyorum. Simdilik secimi dosyanin belirli noktalarindan baslayip 1000 okuma alarak yapiyorum.
