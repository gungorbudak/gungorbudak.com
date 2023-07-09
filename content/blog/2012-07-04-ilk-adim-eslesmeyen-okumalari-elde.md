---
author: Güngör Budak
date: '2012-07-04T19:48:00.001+03:00'
slug: ilk-adim-eslesmeyen-okumalari-elde
tags:
- extract unmapped reads
- eşleşmeyen okuma
- çift-sonlu okuma
- perl
- unmapped reads
- mapped reads
- paired-end reads
- eşleşen okuma
- single-end reads
- tek-sonlu okuma
- fastq
title: 'İlk Adım: Eşleşmeyen Okumaları Elde Etmek'
year: '2012'
---

Projemin ilk kısmı daha önce bahsettiğim gibi eşleşmeyen okumaları (unmapped reads) FASTQ dosyasından çıkarmak. Böylece, daha sonraki analizler için elimdeki ihtiyacım olmayan dizileri çıkarmış ve bu analizlerdeki iş yükünü azaltmış oluyorum.

Başından beri hedefim, tüm projeyi adım adım gerçekleştiren bir pipeline tasarlamak olduğu için bu işlemi bir Perl scripti ile yapacağım. Bu script pipeline'in ilk scripti ve laboratuvardan gelecek ham (raw) FASTQ formatındaki verinin girdi (input) olarak kullanılacağı yer. Aslında bu scripte ihtiyacım olmayacak, sadece elimdeki verinin eşlenebilen verileri de içermesi sebebiyle bu adımı ekledim.

Scripti yazdığım platform bir Unix bilgisayarı, bu yüzden pipeline komut satırından birkaç parametre ile birlikte çalıştırılıyor olacak, yani bazı parametreleri komut satırından gönderecegim. Bu parametreler, okuma türü, FASTQ dosyası ya da dosyaları.

Okumalar iki tür olabiliyor: tek-sonlu okuma (single-end read), çift-sonlu okuma (paired-end read). Tek-sonlu okuma DNA'nın sadece bir sonundan başlanarak tamamının dizilenmesi demek ve çift-sonlu okuma ise DNA'nın her iki sonundan da dizilemenin gerçekleştirilmesi anlamına geliyor. Bu yüzden tek-sonlu okuma tek bir FASTQ dosyasına sahipken, çift-sonlu okumada ise iki FASTQ dosyasıyla çalışıyorum. İşte bu yüzden kullanıcıdan (tek-sonlu okuma için) "se" ya da (çift-sonlu okuma için) "pe" olarak iki türden birini ilk parametre olarak belirtmesini istiyorum. Ardından da kullanıcıdan FASTQ dosyalarının adreslerini eklemesini bekliyorum. Elbette bunu kontrol etmenin birçok yolu var. Şimdilik böyle başladım, ileride daha da kolaylaştırıcı şekilde değiştirebilirim.

Kullanıcı bu parametrelerde Perl scriptini çalıştırdıktan sonra, program aldığı parametrelerle bir dizi işlem sonunda sadece eşleşmeyen okumalariı içeren FASTQ dosyasını ekrana standart çıktı (standard output) olarak yazdırıyor. Aşağıda örnek komutu görüyorsunuz.

```bash
perl extract_unmapped_reads.pl pe hs_sequencing_1.fastq hs_sequencing_2.fastq
```

İşte böylece Perl scripti çalıştırılmış oluyor.

Bir sonraki yazımda scriptin ayrıntılarına, bwa, samtools gibi kullandığım diğer komutlara değineceğim.
