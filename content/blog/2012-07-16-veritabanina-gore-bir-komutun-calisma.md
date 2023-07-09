---
author: Güngör Budak
date: '2012-07-16T04:17:00.000+03:00'
slug: veritabanina-gore-bir-komutun-calisma
tags:
- cpu runtime
- nrnuc
- refseq_genomic
- ensembl_cdna
- megablast
- honest
title: Veritabanina Gore Bir Komutun Calisma Suresi - CPU Runtime
year: '2012'
---

Calisilan dosyalar, veritabanları buyuk olunca ve yeterince bilgisayar gucune sahip olmayınca, her seyden once olcmemiz gereken nasil en etkili ve kisa surede sonucu alabiliyor olmamizdir.

Özellikle projemde, farkli veritabanları ve farkli parametreler kullanarak, bunları arastiriyorum.

Şimdilik dort veritabani deniyorum, bunlar: nrnuc, ensembl_cdna, honest ve refseq_genomic. Ayrica, bunu farkli iki kelime uzunluğuna gore de yapacagim. Kelime uzunluğu (word size) MegaBLAST'in ararken tam olarak eslestirecegi baz cifti sayisi. Yani elimde 151 baz ciftine sahip bir dizilim varsa, ve eger kelime uzunluğu 50 olarak belirlenmişse, bu 151 baz cifti icinden herhangi bir yerden baslayan ama arka arkaya en az 50 bazin dizilendiği kisimlar aranacak.

Bu veritabanlarinin farkli sonuclar vermesi elbette sahip oldugu dizi sayisina ve bunlari buyuklugune bagli. Projemde ben DNA dizisinden, herhangi bir tahminim olmadan, direkt olarak veritabanindan olasi organizmalari aradigim icin bana yeterince genis ve iyi sonuclar verebilecek bir veritabani gerekiyor. Belki iki veritabanini birlikte de kullanabilirim, ancak tum bunlari belirlemeden once veritabanlarini tek tek arastirmam gerekiyor.

Bu veritabanlari ile ilgili arastirmalarimi da gene birer yazi olarak yayinlayacagim.
