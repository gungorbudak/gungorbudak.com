---
author: Güngör Budak
date: '2012-07-13T09:29:00.000+03:00'
slug: veritabani-secimi
tags:
- ncbi
- refseq
- ensembl_cdna
- honest
- reference sequence
title: Veritabani Secimi
year: '2012'
---

Bu projedeki amacim olasi kirleten organizmalari (kontaminantlari)  bulmak. Dolayisiyla genis bir veritabanina ihtiyacim var. Ancak  veritabanini genis tutmak boyle bir avantaj sagliyorken, her dizi icin o  veritabaninda arama yapmak oldukca fazla bilgisayar gucu ve zaman  gerektiriyor. Bu yuzden projemi gelistirirken, cesitli veritabanlarini  da inceliyorum. Ve ayrica bunlari nasil kisitlayarak, amacim icin en  uygun hale getirebilecegimi arastiriyorum.

Ilk olarak NCBI'in Reference Sequence (Kaynak Dizi ya da Referans  Sekans) -- RefSeq -- veritabaniyla basladim. RefSeq, cok genis, iyi  adlandirilmis, plazmid organel, virus, arke, bakteri ve ökaryotlarin  DNA, RNA ve protein dizilerini barindiriyor.<sup>1</sup> Ben RefSeq'in genomik  kismiyla calisiyorum ve o da gene oldukca genis bir veritabani. Komut  satirinda yaptigim olcume gore 151 baz ciftinden olusan her okumanin  RefSeq'te aranmasi ortalama 5 dakika aliyor ve CPU %50 oraninda  kullaniliyor. Elbette ilk aramada sunucu veritabanini sakladigi icin  biraz daha fazla zaman geciyor (yaklasik 8 dakika) ancak birden fazla  yapilan aramalarda ortalamada bu sayi dusuyor. Ayrica eger CPU'nun  tamamini kullanabilirse, herbir okuma, tahmini 5 dakikadan daha az  aliyor diyebiliyoruz. Eger boylece tum kaynaklari yeterli  kullanabilirsek ve islemleri paralel calisacak sekilde tasarlarsak, bir  hafta sonu gunu (tahmini sunucunun en az kullanilacagi zaman dilimi)  yaklasik 2500 okuma aranabilir.

2500 okuma ne yazik ki toplam sayi olan 5.5 milyonu dusundugumuzde  cok kucuk bir sayi. Bu yuzden okumalari paralel bicimde aratarak daha  fazla hiz kazanmayi hedefliyorum. Yani, 1 milyonuncu okumadan baslayip  2500 okuma kadar arama yapmasini istiyorum ve bu islemi arkaplana  atiyorum, daha sonra bir islem daha baslatiyorum ve bu sefere 1,002,500.  okumadan baslayip 2500 okuma kadar aratiyorum. Boylece toplamda 8  paralel islem ile, isleri mumkun oldugunca hizlandirabiliyoruz.

Ancak gene de yetmiyor, hala bu genis veritabanina bir alternatif  bulmak gerekli. Eger, yerine gecebilecek, ise yarar ama daha kucuk bir  veritabani bulabilirsem, her sey daha cabuk yapilabilir.

RefSeq ile birlikte HUSAR tarafindan olusturulan honest ve Ensembl'in cDNA veritabani var. Simdilik dizileri bunlarda da arayip, karsilastirmalar yapiyorum.

**Kaynaklar**

1. The Reference Sequence (RefSeq) Database, <a href="http://www.ncbi.nlm.nih.gov/books/NBK21091/" target="_blank">http://www.ncbi.nlm.nih.gov/books/NBK21091/</a>
