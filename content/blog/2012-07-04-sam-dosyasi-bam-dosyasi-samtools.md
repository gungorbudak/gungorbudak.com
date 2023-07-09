---
author: Güngör Budak
date: '2012-07-04T20:36:00.003+03:00'
slug: sam-dosyasi-bam-dosyasi-samtools
tags:
- bam2fastq
- megablast
- samtools
- fastq
- bwa
- eşleşmeyen okuma
- samtools view
- bam
- husar
- sam
- eşleşen okuma
- fasta
title: SAM Dosyası - BAM Dosyası - samtools
year: '2012'
---

Aslında programlamam gereken pipeline direkt olarak eşleşmeyen okumalar üzerinden analizler yapacak. Ancak böyle bir veri bulamadiığım için, elimdeki tek veri eşleşen ve eşleşmeyen okumaları içerdiği için önce eşleşenlerden kurtulmam gerekti.

Bunu daha önce de belirttiğim gibi bwa eşleştiricisi (aligner - mapper) ile yapıyorum. bwa bir dizi işlemden sonra SAM dosyası oluşturuyor ancak benim FASTQ dosyasına ihtiyacım var. Bunun için SAM dosyasını samtools<sup>1</sup> ile benzer bir format olan BAM dosyasına çevirip, daha sonra da bam2fastq<sup>2</sup> aracı ile FASTQ dosyamı elde edeceğim.

SAM dosyasında, tahmin edebileceğiniz gibi sıralamalar (alignment) var. Ve her sıralama 11 satıra sahip ve bu satırlar sıralama, sıralayıcı (eşleştirici - aligner) ilgili bilgiler içeriyor. Bu satırlardan üçüncüsü sıralamanın ismi, onuncusu sıralamanin dizilimi (ya da sekansı) ve on birincisi ise sıralamalanın kalitesi. İşte bu alanlar özellikle FASTQ dosyası için gerekli, elbette diğer bilgiler de başka yerlerde öneme sahipler. BAM dosyası ise SAM dosyasının ikilik sistemde (binary) sürümü.

Aşağıdaki kod ile samtools komutunun view seçeneği üzerinden -S (girdisi SAM dosyası) ve -b (çıktısı BAM dosyası) parametreleriyle dosyanızı çevirebiliyorsunuz.

```bash
samtools view -Sb dosya.sam > dosya.bam
```

Daha sonra HUSAR paketinde bulunan, <a href="http://www.hudsonalpha.org/gsl/software/bam2fastq.php" target="_blank">ücretsiz olarak elde edilebilecek</a> bam2fastq komutu ile BAM dosyasını FASTQ dosyasına çevirerek işlemi tamamlıyoruz. Burada --output parametresi ile FASTQ dosyasının adını, --unaligned ve --no-aligned parametreleri ile de sadece eşleşmeyen okumaları almasını sağlıyoruz.

```bash
bam2fastq --output dosya_%#.fastq --unaligned --no-aligned dosya.bam
```

Sırada bu FASTQ dosyasını FASTA dosyasına çevirip, MegaBLAST ile aradıktan sonra çıktılar incelemek (parsing) var.

**Kaynaklar**

1. The Sequence Alignment/Map format and SAMtools, <a href="http://www.ncbi.nlm.nih.gov/pubmed/19505943">http://www.ncbi.nlm.nih.gov/pubmed/19505943</a><br />
2. bam2fastq, <a href="http://www.hudsonalpha.org/gsl/software/bam2fastq.php">http://www.hudsonalpha.org/gsl/software/bam2fastq.php</a>
