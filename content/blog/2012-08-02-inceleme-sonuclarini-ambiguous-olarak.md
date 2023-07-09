---
author: Güngör Budak
date: '2012-08-02T06:03:00.000+03:00'
slug: inceleme-sonuclarini-ambiguous-olarak
tags:
- ambiguous hit
- hash
- perl
- tek
- megablast
- value
- anahtar
- unique hit
- değer
- çok anlamlı
- key
- belirsiz
- eşsiz
title: Inceleme Sonuclarini "Ambiguous" Olarak Ayirmak
year: '2012'
---

Cesitli veritabanlarina karsi yaptigim aramalardan aldigim sonuclari incelerken, bunlari cesitli esik degerleri ile degerlendirmek ile beraber belirlenen esik degerlerinin uzerinde ya da altinda olan hitleri "Ambiguous" (belirsiz, cok anlamli) ya da "Unique" (essiz, tek) olarak ayirarak daha da anlamli hale getirmeye calisiyorum.

"Ambiguous" olarak, her bir megablast dosyasinda esik degerlerine uygun ancak birden fazla farkli organizmayi iceren hitleri etiketliyorum. Eger her esik degerine uygun hit, tek bir dosya icinde her zaman ayni organizmaya ait ise bu durumda yaptigim sey onu "unique" olarak etiketlemek.

Perl ile "Ambiguous" ve "Unique" icin birer hash tanimliyorum ve organizma isimlerine gore bu hashlerdeki anahtarlarin degerini artiritorum. Sonunda da bu iki etikete ait toplamlari liste olarak gosteriyorum.

Bunun bir ornegi aslinda <a href="{{ site.baseurl }}{% post_url 2012-08-02-ikinci-veriseti-inceleme-sonuclari %}" target="_blank">ikinci veriseti incelemesi</a>nde var, ancak bunda "Ambiguous" hitleri sadece bir organizmaymis gibi kabul ediyorum ve hangi organizmalarin oldugunu gostermiyorum. Inceleme scriptinde yaptigim diger bir desigisiklikle daha fazla bilgi edinmek, "Ambiguous" hitlerin icerini ve organizma dagilimini gormek icin tek tek bunda bulunan organizmalari sayiyorum. Direkt buna ornek ucuncu verisetinin incelemesiyle gelecek.
