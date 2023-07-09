---
author: Güngör Budak
date: '2012-07-23T04:19:00.000+03:00'
slug: duzenli-ifadeler-ile-tur-ismini-elde
tags:
- getz
- ncbi
- refseq
- refseq_dna
- düzenli ifadeler
- megablast
- srs
- reference sequence
- regular expressions
- sequence retrival system
- husar
- unix
title: Duzenli Ifadeler ile Tur Ismini Elde Etmek
year: '2012'
---

Projemin sonunda kullaniciya olasi kirleten organizmalarin adlarini (Latince tur isimleri) gosterecegim icin, MegaBLAST sonuclarindaki erisim numaralarini (accession number) kullanarak her dizi icin organizma adlarini elde etmem gerekiyor. Sequence Retrival System (SRS) adinda, HUSAR sunucularinda bulunan baska bir sistem ile bunu yapabiliyorum.

SRS'ten organizma adini ogrenebilmem icin Unix komut satirinda "getz" komutuyla birlikte veritabani ismi, erisim numarasi ve ogrenmek istedigim alani yazmam yetiyor. Asagida, bu isi yapabilen ornek bir kod bulabilirsiniz.

```
getz "[refseq_dna:NW_001840913]" -vf "ORGANISM"
```

Yukaridaki kod parcasinda "getz" komutumuz, "refseq_dna" NCBI'in Reference Sequence veritabani, "NW_001840913" erisim numarasi, "-vf" alanlari gostermemizi saglayan parametre ve son olarak "ORGANISM" de -vf parametresine bagli, bize organizma ismini verecek arguman.

Bu komut satiri, asagidaki ciktiyi veriyor.

```
REFSEQ_DNA:NW_001840913 Homo sapiens
```

Ve bu ciktiyi kullanarak, "REFSEQ_DNA:NW_001840913" ve hemen sonundaki TAB karakterinden kurtulmak ve kalan kismini bir degiskene atayip, gostermek gerekiyor. Bunu da asagidaki duzenli ifade ile yapiyoruz.

```
$params[0] =~ /\t(.*)/;
$params[0] = $1;
```

Bu kodda `$params[0]` getz komutunun ciktisini saklayan degisken. Bu degiskende saklanan tur ismini `\t` (TAB) karkaterinden sonra bulunan herhangi birden fazla karakter ifadesiyle `(\.*)` alip, tekrar ayni degiskene, bunu atiyoruz.

Asagidaki kod, inceleme yapan scriptin bir bolumunden alinmis, refseq veritabaninda organizma ismini almak icin yazdigim kisma ait.

```
elsif ($database eq "refseq_dna") {
    $params[0] =~ /:([A-Z|0-9]*\_[A-Z|0-9]*)/;
    $params[0] = $1;
    $params[0] = `getz "[$database:$params[0]]" -vf "ORGANISM"`;
    $params[0] =~ /\t(.*)/;
    $params[0] = $1;
}
```

Bu kod parcasini her megablast dosyasindan okudugumuz dizi ismi icin dondurdugumuzde, tur isimlerinin bulundugu bir listeyi elde edebiliriz. Bu elsif yapisi icinde gorunen diger duzenli ifade de erisim numarasini, getz komutunda kullanmak uzere elde etmemizi sagliyor.

Ayrica bu yapida getz komutunun ciktisini, direkt olarak bir degiskene backtick, "`", karakteri kullanarak atadigimi vurgulamak istiyorum. system komutundan sonra, bu Perl ile dis komutlari calistirmanin baska bir yolu.

Elbette bu yazida inceleme yapan scriptin diger kisimlari yok, onlari da ekledigimde tamamina bakabilirsiniz.
