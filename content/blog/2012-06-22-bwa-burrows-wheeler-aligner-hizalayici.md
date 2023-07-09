---
author: Güngör Budak
date: '2012-06-22T19:21:00.000+03:00'
slug: bwa-burrows-wheeler-aligner-hizalayici
tags:
- dkfz
- bwa
- insan genomu
- burrows-wheeler aligner
- bwa mapper
- hizalıyıcı
- eşleştirici
- genom eşleştirici
- accuracy
- mapper
- structural variations
title: BWA (Burrows-Wheeler Aligner) Hizalayıcı - Eşleştirici
year: '2012'
---

Önceki yazımda belirttiğim gibi bir eşleştirici (aligner ya da mapper) kullanarak elimdeki verinin referans genomu ile ne derece eşlestiğini bulmaya çalışacağım. Daha sonra eşleşmeyen kısmıyla birtakım analizler yapacağım.

BWA (Burrows-Wheeler Aligner) görece kısa dizilimleri insan genomu gibi uzun referans genomlarıyla eşleştiren bir program. 200bp (bp: baz çifti) uzunluğuna kadar bwa-short algoritması, 200bp - 100kbp arası ise BWA-SW algoritması kullanılıyor.

Hizalayıcı - eşleştirici seçmede birçok faktör rol oynuyor. Birçok bu tip araç var ve farklı özelliklere sahipler. Bunlar performans ve hassasiyet (accuracy) özelliklerine göre değişiyor. Ayrıca hassasiyet, yapısal varyasyonları (structural variations - SVs) da etkiliyor.

İleride bu programın özelliklerine daha fazla değineceğim.
