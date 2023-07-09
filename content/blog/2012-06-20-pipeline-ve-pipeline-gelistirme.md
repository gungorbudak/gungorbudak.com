---
author: Güngör Budak
date: '2012-06-20T13:12:00.000+03:00'
slug: pipeline-ve-pipeline-gelistirme
tags:
- pipeline
- biyoenformatik
- dkfz
- pipeline development
- w2h
- husar
- pipeline geliştirme
- erasmus
title: Pipeline ve Pipeline Geliştirme
year: '2012'
---

Bugün aldığım tanıtım derslerinin devamında, pipeline ve pipeline geliştirme ile ilgili ayrıntılı bilgiler aldım. Pipeline, aslında bildiğimiz boru hattı demek, örneğin borularla petrolün bir yerden başka bir yere taşınması için kullanılan sistem. Bunun bilgisayar terminolojisinde anlamı ise bir elementin çıktısı, diğerinin girdisi olacak şekilde oluşturulmuş işleme elementleri zinciri. Böylece çok daha komplike işlemler pipeline oluşturularak, kolay ve düzenli bir biçimde gerçekleştiriliyor. Sanırım pipeline Türkçeye ardışık düzen olarak çevriliyor, gene de ben pipeline olarak kullanacağım.

Pipeline oluşturulması birkaç adım içeriyor. Öncelikle işlem öncesi (pre-processing) yapılması gereken kontroller var, bunlar örneğin JavaScript gibi client-side bir dil ile yapılabiliyor. Amaç, kullanıcının girdilerini kontrol etmek ve henüz işlemeden herhangi bir olası uyumsuzluğu, hatayı önceden bildirmek ve kullanıcıyı uyarmak. İşlem süresince ise pipeline, gelen verinin analizini yapıyor, eğer ileride tekrar kullanmak ıstıyorsak saklıyor ve bunu çözümledikten sonra çıktı olarak veriyor. Son, çıktı adımında ise en iyi gösterim için stil dosyaları kullanılıyor ve çıktı XML dosyasına dönüştürülerek, daha sonra kolayca kullanılabilecek bir formatta gösteriliyor.

XML'e dönüştürme gerçekten çok önemli, çünkü böylece hem makina, hem de insanın okuyabileceği bir formatta sonuçlarınızı sunabiliyorsunuz. XML (Genişletilmiş İşaretleme Dili) verileri sizin belirleyebileceğiniz etiketler ve özelliklerle saklamanızı sağlayan bir standart.
