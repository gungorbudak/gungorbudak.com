---
author: Güngör Budak
date: '2012-07-06T19:46:00.000+03:00'
slug: eslestirme-ve-eslesmeyen-okumalari
tags:
- bwa
- eşleşmeyen okuma
- eşleşmeyen okumaları çıkarmak
- eşleşen okuma
- fastq
title: Eşleştirme ve Eşleşmeyen Okumaları Çıkarma Sonuçları
year: '2012'
---

Daha önce verinin sadece bir kısmı ile çalışıyordum ancak artık tamamıyla çalışacağım. Bu yüzden bana sıkıştırılmış halde gelen veriyi direkt çalışma klasörüme çıkardım ve onun üzerinden işlemler yaptım.

Başlangıç (FASTQ) dosyamın boyutu 2153988289 bayt (2 GB). Ve bwa aracılığıyla eşleştirmeden sonra toplamda 6004193 dizilim, ya da okuma, (sequences ya da reads) ortaya çıktı. Daha sonra eşleşmeyen okumaları çıkarmam sonrasında toplam okuma sayısı 551065 kadar azaldı ve 5493128 oldu. Yani verinin %9.2'si eşleşeşen okumalara, kalan kısmı ise eşleşmeyen okumalara ait. Eğer her şey yolundaysa, bu sayı elimdeki eşleşmeyen okuma sayısı. Ve bu sadece eşleşmeyen okumaları içeren FASTQ dosyasının boyutu 1932192710 bayt (1.8 GB), yani orijinal dosyanın boyutu 221795579 bayt (0.2 GB) kadar azaldı.

Aslında bu kadar fazla eşleşemeyen okuma beklemiyordum. Elbette elimdeki veri böyle bir sonuç vermiş olabilir, çünkü "kötü" bir veri olduğu bana söylenmişti. Gene de kullandığım yöntemi deneyeceğim ve daha fazla araştırmayla bu sonucu yorumlamaya çalışacağım.
