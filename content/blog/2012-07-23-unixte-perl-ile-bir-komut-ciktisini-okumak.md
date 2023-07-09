---
author: Güngör Budak
date: '2012-07-23T05:06:00.001+03:00'
slug: unixte-perl-ile-bir-komut-ciktisini-okumak
tags:
- getz
- perl
- düzenli ifadeler
- megablast
- srs
- unix
title: Unix'te Perl Ile Bir Komut Ciktisini Okumak ve Duzenli Ifadeler
year: '2012'
---

Daha once organizma isimlerini duzenli ifadelerle nasil cikardigimi anlatmistim. Burada, gene benzer bir seyden bahsedecegim ancak bu biraz daha fazla, ozel bir teknikle Perl'de yapilan, veri tabanindan bilgileri birden fazla satir halinde cikti olarak aldigim icin gerek duydugum cok yararli bir yontem. Mutlaka benzerini baska amaclarla da kullanabilir, yararlanabilirsiniz.

Bu ihtiyac, HUSAR gurubu tarafindan olusturulan honest veritabaninin organizma isimlerini direkt sunmamasi ancak birkac satir halinde gostermesi sebebiyle dogdu. Asagida bunun ornegini gorebilirsiniz. 

```bash
HUSAR %getz "[emblall:EU025714]" -f "ORGANISM"
OS   Salmo salar (Atlantic salmon)
OC   Eukaryota; Metazoa; Chordata; Craniata; Vertebrata; Euteleostomi;
OC   Actinopterygii; Neopterygii; Teleostei; Euteleostei; Protacanthopterygii;
OC   Salmoniformes; Salmonidae; Salmoninae; Salmo.
```

Ilk satirda, organizmanin tur ismini ve parantez icinde de yaygin olarak kullanilan ismini goruyoruz. Ayrica TAB, "\t", ile birlikte basinda "OS" karakterleri bulunuyor. Iste bu ciktiyi Perl'de sanki bir dosya okuyormus gibi bir dongu icinde okuyarak, ilk satiri ve ilk satirdan da sadece tur ismini alacagiz.

```perl
elsif ($database eq "emblall") {
    $params[0] =~ /:([A-Z|0-9]*)\_?/;
    $params[0] = $1;
    open (PIPE, "getz '[$database:$params[0]]' -f 'ORGANISM' |") or die $!;
    while(my $line = <PIPE>) {
        $line =~ /^OS\s+(\w+)\s+(\w+)/;
        $params[0] = "$1 $2";
        }
    close PIPE;
    }
```

Yukaridaki `elsif` yapisi ile, oncelikle her zaman oldugu gibi getz komutunda kullanmak uzere okuma (ya da dizi) isminden erisim numarasini (anahtarini) bir duzenli ifade ile aliyorum. Bu duzenli ifade, veritabalarinin dizi isimlerini nasil sunduguna gore degistigi icin, her veritabani icin ayri bir elsif yapisinda, farkli duzenli ifadeler yaziyorum. Daha sonra bu erisim numarasini degiskende sakladiktan sonra open fonksiyonu ile "getz"in verdigi ciktiyi "aciyoruz" (sanki bir dosya okuyormus gibi...). Burada tek fark, getz komutunun sonuna boru (pipe), \|, karakterini de ekliyoruz. Perl'de bu hile tam olarak boyle yapiliyor. Daha sonra gene her zaman oldugu gibi bir while dongusu ile (aslinda sadece bir cikti olan) "dosyamizi" satir satir okuyoruz. Sadece bir satirla ilgilendigimiz icin, bu satiri baska bir duzenli ifade ile ayiriyor ve sadece organizme ismini elde ediyoruz. Daha once de belrttigim gibi organizma isminin bulundugu satirda "OS" ve "\t" karakterleri ile birlikte, bir de bosluk, "\s", ve parantez icin organizmanin yaygin kullanilan ismi var. Elbette tur ismi cins ismi, bosluk ve tur adi seklinde yazildigi icin "(\w+)\s+(\w+)" ifadesiyle $1 degiskeninde orgizmanin cinsini, $2 ifadesinde de tur adini sakliyoruz. Duzenli ifadedeki "\w", bosluk disinda herhangi bir karakter anlamina geliyor ve sonuna arti, "+" ekleyerek bu karakterlerden birden fazla olabilecegini belirtiyoruz. Son olarak da actigimiz "PIPE" dosyasini close fonksiyonu ile kapatiyoruz.

Boylece, birkac satirdan olusan bir ciktidan, sadece organizmanin tur ismini elde ederek, raporda sunabiliyorum.
