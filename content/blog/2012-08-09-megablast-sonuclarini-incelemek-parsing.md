---
author: Güngör Budak
date: '2012-08-09T09:14:00.001+03:00'
slug: megablast-sonuclarini-incelemek-parsing
tags:
- parsing
- emacs
- hash
- perl
- script
- megablast
- unix
title: MegaBLAST Sonuclarini Incelemek - Parsing
year: '2012'
---

Pipeline'da son asama, aranan dizilerin urettigi ciktilari baska bir script ile incelemek. Bu islemle herbir megablast dosyasi okunuyor, ve dizilerin name, identity, overlapping length gibi parametrelerinin degerleri saklanarak amaca yonelik sekilde ekrana yazdiriliyor.

Projemde HUSAR paketinde bulunan ve yukarida bahsettigim alanlari bana dizi olarak donduren Inslink adinda bir parser kullaniyorum. Bu parserin yaptigi tek sey, dosyayi okumak ve dosyadaki istenen alanlarin degerlerini saklamak.

Daha sonra ben bu saklanan degerleri, koda eklemeler yaparak gosteriyorum ve birkac ek kod ile de ihtiyacim olan anlamli sonuclar gosteriyorum.

Gene bu scripti de Unix uzerinde Emacs yazilimini kullanarak Perl dilinde yazdim.

Script parserdan gelen bilgileri kullanarak once esik degeri kontrolu yapiyor ve gecen tum okumalarin organizma ismini getz komutuyla alarak bir hash icinde saklayip sayarak bunlari daha sonra ekrana yazdiriyor. Boylece esik degerini gecen organizma sayisi uzerinden yorum yapabiliyorum.

Bu scripti projenin gelisme asamasinda cokca degistirdim. Farkli genomlari arastirirken farkli ihtiyaclar ciktigi icin her seferinde bir yenilik ile daha guvenilir hale geliyor. Daha oncekilero yazmayacagim ama su an son olarak kodladigim scripti paylasacagim.
