---
author: Güngör Budak
date: '2012-06-27T11:24:00.000+03:00'
slug: kontaminant-kirletici-analizi-projesi
tags:
- tel aviv üniversitesi
- biyoenformatik
- dkfz
- dna dizisi
- kirletici analizi
- kontaminant analizi
- husar
- megablast
- fasta
- fastq
title: Kontaminant (Kirletici) Analizi Projesi
year: '2012'
---

Başlangıç olarak, araçlara, programlama diline, kısacası biyoenformatiğe alışabilmem için bana verilen bu ufak projeyi ayrıntılı olarak anlatacağım.

Biliyoruz ki, laboratuvar çalışmalarımızda ne kadar önlemeye çalışsak da kontaminant riski hep bulunuyor. Bunu ne kadar aza indirsek o kadar iyi, ki daha sonra bunun miktarını bulup, bunun üzerinden sonucumuzun bir başka değerlendirmesini de yapabiliriz. İşte bunu bulmak için bir yöntem, DNA analizi. Çalıştığınız örneğinizin DNA'sı dizileniyor ve bu DNA çeşitli programlarla analiz edilip, kirleten organizmaları DNA'larından ortaya çıkarabiliyoruz

Literatür araştırması sonrası bu tarz programlar olduğunu gördüm ancak daha farklı açıdan yaklaşmışlar. Örneğin Tel Aviv Üniversitesi'nden bir grup, benzer bir çalışmayı insanda patojen enfeksiyonlarını bulma ve buradan tedavi geliştirme konusunda gerçekleştirmişler.<sup>1</sup>

Bu proje birkaç Perl scriptinin oluşturulmasını içeriyor. Bunların ilki, DNA diziliminin bir referans genomuyla karşılaştırılarak, eşleşebilen kısmının çıkarılması ve kalan kısmın FASTQ formatında kaydedilmesi. Daha sonra bu dosya, sonraki adımlar için FASTA formatına bir başka Perl scripti ile dönüştürülecek. Ardından Bu FASTA dosyası, MegaBLAST aracı ile taranacak ve sonuçlar kaydedilecek. Ve şimdilik son olarak da bu sonuçlar değerlendirilecek.

Proje yapım aşamasında değişebiliyor, ufak eklentiler gelebiliyor. Şu an için bu şekilde planlandı. Projeyle ilgili diğer ayrıntıları, devam ederken diğer yazılarda vereceğim. Özellikle her adımlar neleri uyguladığımı yazmak ve böylece benzer işleri yapacak arkadaşlarım için bir kaynak oluşturmayı düşünüyorum.

**Kaynaklar**

1. Pathogen detection using short-RNA deep sequencing subtraction and assembly,&nbsp;<a href="http://bioinformatics.oxfordjournals.org/content/27/15/2027.full">http://bioinformatics.oxfordjournals.org/content/27/15/2027.full</a>
