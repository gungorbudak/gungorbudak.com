---
author: Güngör Budak
date: '2012-07-06T19:40:00.002+03:00'
slug: bwa-ile-eslestirme-mapping-alignment
tags:
- sai
- aln
- mapping
- bwa
- insan genomu
- alignment
- eşleşmeyen okumaları çıkarmak
- eşleştirme
- samse
- human genome
- fastq
title: BWA İle Eşleştirme (Mapping - Alignment)
year: '2012'
---

Bunu daha önce yazmayı unutmuşum. Aslında bahsetmiştim ancak nasıl yapıldığına dair bir şeyler yazmamışım ayrıca örnek komutlar da eklememişim.

BWA elimizdeki (FASTQ formatındaki) DNA dizilimini, referans genomunu (projemde bu insan genomu) alarak bir .sai dosyası oluşturuyor. Bu dosya dizinin ve referans genomunun eşleşmesi ile ilgili bilgiler taşiyor ve bu bilgileri kullanarak eşleşmeyenleri ayırabiliyorum.

İlk olarak aşağıdaki komut ile .sai dosyamızı oluşturuyoruz.

```bash
bwa aln $NGSDATAROOT/bwa/human_genome37 ChIP_NoIndex_L001_R1_complete_filtered.fastq > complete_alignment.sai
```

Oluşturduğumuz .sai dosyası çok da kullanışlı bir dosya değil, bu yüzden onu SAM dosyasına çevirerek, işlemlere devam ediyoruz. Elimizdeki veri tek-sonlu okuma (single-end read) olarak kabul edildiği için "samse" ile bu değişimi yapıyoruz, eğer çift-sonlu okuma (paired-end read) olsaydı "sampe" kullanılacaktı.

Bunu da aşağıdaki kod ile gerçekleştiriyoruz.

```bash
bwa samse $NGSDATAROOT/bwa/human_genome37 complete_alignment.sai ChIP_NoIndex_L001_R1_complete_filtered.fastq > complete_alignment.sam
```

Bundan sonra elde ettiğimiz SAM dosyasıyla çalışmamıza devam ediyoruz. Devamı aşağıdaki yazımda bahsettiğim BAM dosyasına dönüştürme ve ardından FASTQ dosyasına çevirme var.

İlgili yazı: [SAM Dosyası - BAM Dosyası - samtools]({% post_url 2012-07-04-sam-dosyasi-bam-dosyasi-samtools %})
