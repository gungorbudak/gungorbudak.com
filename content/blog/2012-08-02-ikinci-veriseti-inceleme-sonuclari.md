---
author: Güngör Budak
date: '2012-08-02T05:15:00.001+03:00'
slug: ikinci-veriseti-inceleme-sonuclari
tags:
- dataset
- refseq
- refseq_genomic
- veriseti
- refseq_dna
- perl
- homo sapiens
title: Ikinci Veriseti Inceleme Sonuclari
year: '2012'
---

Daha az eslenemeyen okumalara sahip ikinci verisetinin incelemesini tamamladim. Bu oncekine gore daha iyi bir dizileme ornegi oldugu icin aldigim sonuclar da oldukca tutarliydi. Insan genomuna ait bir diziden inceleme sonra asagidaki sonuclari elde ettim.

```
LIST OF ORGANISMS AND THEIR NUMBER OF OCCURENCES
Ambiguous hit   1323
Homo sapiens    312
Pan troglodytes 25
Pongo abelii    18
Nomascus leucogenys     17
Halomonas sp. GFAJ-1    7
Callithrix jacchus      4
Macaca mulatta  3
Oryctolagus cuniculus   2
Loxodonta africana      1
Cavia porcellus 1
```

"Ambiguous hit" tanimini baska bir yazida aciklayacagim. Simdilik sadece onlarin da bir hit oldugunu soylemem ve bu hitlerin de esik degerlerini gecmis oldugunu belirtmem yeterli olacak.

Yukaridaki sonuc RefSeq genomik veritabani aramasina dayali bilgiyi iceriyor ve birkac insana uzak okaryot ve bakteri disinda cogunlukla insan ve diger maymunlara ait sonuclar almam sonucun tutarli oldugunu gosteriyor. Aslinda daha onceki yazilara gozattiysaniz, sonuclarda "Homo sapiens" gormememiz gerektigi dusunebilirsiniz. Cunku bana gelen verisetinin insan genomuna karsi eslestirildigini ve eslesebilenlerin cikarildigini soylemistim, eger bana gelen veri her ikisini de iceriyorsa ben onlari baska bir araclar cikariyorum ki daha sonra karsima cikmasinlar ve olasi kirletici organizmalari direkt gorebileyim. Ancak buna ragmen sonuclarda *Homo sapiens* de goruyoruz. Aciklamayi eslestirme icin kullandigimiz araci inceleyerek bulmaya calistik ve su ki bwa araci eslesmeyen bazlara (mismatch) yeterince duyarli olmadigi bu sonucu aldik. Bu direkt olarak bwa ile ilgili ve onun kullandigi algoritmanin yarattigi bir durum. Elbette bizim icin bir sorun yaratmiyor, bunu bilerek zaten birtakim *Homo sapiens* hitleri bekliyoruz.

Bu verisetiyle birlikte inceleme yapan Perl scriptinde -- "Ambiguous hit" eklentisini de iceren -- bazi degisiklikler yaptim, onu ayrica aciklayacagim.
