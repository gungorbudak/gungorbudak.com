---
author: Güngör Budak
date: '2012-07-13T05:05:00.002+03:00'
slug: fastqdan-fastaya-donusturme-perl
tags:
- while
- fastq fasta conversion
- perl
- fastq fasta dönüştürmek
- script
- megablast
- fasta
- fastq
title: FASTQ'dan FASTA'ya Donusturme Perl Scripti
year: '2012'
---

FASTQ ve FASTA formatlari aslinda ayni bilgiyi iceren ancak birinde sadece  herbir dizi icin iki satir daha az bilginin bulundugu dosya formatlari.  Projemde onemli olan diger bir farklari ise FASTA formatinin direkt  olarak MegaBLAST arama yapilabilmesi. Iste bu yuzden, genetik dizilim  yapan makinelerin olusturdugu FASTQ formatini FASTA'ya cevirmem  gerekiyor. Ve bu script pipeline'in ilk adimi.

Aslinda deneme amacli aldigim genetk dizilimin, bana bunu ulastiran  tarafindan eslestirmesinin yapilmadigi icin, bir on adim olarak bu  eslestirmeyi yapmistim. Ancak, pipeline'a boyle bir adim eklemeyecegim.  Pipeline, icerisinde sadece eslesemeyen okumalarin (unmapped reads)  bulundugu FASTQ dosyasiyla baslayacak.

Asagidaki detaylandirdigim script, create_fasta.pl adini verdigim Perl scripti.

Her zaman oldugu gibi scriptle su satirla basliyoruz:

```perl
#!/usr/local/bin/perl
```

Daha  sonra kullanicidan scripti calistirirken istedigimiz iki parametreyi  @ARGV dizisinden (array) okuyoruz. $input, FASTQ dosyasinin yolu, $n ise  FASTA formatina cevirmek istedigimiz okuma sayisi. Eger tum dosyayi  cevirmek istiyorsak, $n degeri girmeyebiliriz. Bu durumda asagidaki  kontrol yapisindan anlayacaginiz gibi $n tanimlanmadiginda $n'i cok  buyuk bir sayiya (10<sup>12</sup>) atiyor.

```perl
$input = $ARGV[0];
if (defined($n)) {
    $n = $ARGV[1];
} else {
    $n = 1000000000000;
}
```

Ardindan girdi dosyamizi (FASTQ dosyasi) aciyoruz.

```perl
open INPUT, $input or die $!;
```

Sonra  $i, $j ve $k degiskenlerine sirasiyla 1, 2, 1 degerlerini atiyoruz. Bu  degiskenlerden $i her okumanin baslik satirinin, satir numarasi, boylece  her $i'inci satiri, baslik olarak gorup, o sekilde FASTA dosyamiza  yazdirabiliriz. Ayni sekilde $j ise her okumanin dizilim satirinin satir  numarasi, yani her $j'inci satirda bir diziyle karsilasiyoruz. Bu  satirlar her 4 satirda bir karisimiza ciktigi icin (cunku FASTQ  dosyasinda her okuma 4 satira sahip) bunlari daha sonra kontrol  yapilarinin icinde 4'er artiracagiz. $k ise, sadece bir sayici. Her  okumada, kontrol yapisi icinde, 1 artirilacak ve onu okuma adindaki  okuma numarasini yazdirmak icin kullanacagim.

```perl
$i = 1;
$j = 2;
$k = 1;
```

Simdi tum isi yapan while dongusu var. Bu dongu dosyayi satir satir okuyor ve satiri baslik ise ayri, dizi ise ayri degerlendirip ona gore cikti veriyor. Ayrica eger istedigimiz okuma sayisina ulasmissa donguyu sonlandiriyor.

while dongusunu asagidaki gibi kuruyoruz ve dosyamizdaki her okunan satiri $line degiskeninde sakliyoruz. 

```perl
while(my $line = <INPUT>){

}
```

Daha sonra chomp komutu ile bu satirdan, satir sonundaki yeni satir karakterini siliyoruz.

```perl
chomp($line);
```

Son olarak asagida, kodun tumunde goreceginiz while dongusu icindeki kontrol yapilari ile de dosyamizi satir satir olusturuyoruz.

```perl
#!/usr/local/bin/perl
$input = $ARGV[0];
if (defined($n)) {
    $n = $ARGV[1];
} else {
    $n = 1000000000000;
}

open INPUT, $input or die $!;
$i = 1;
$j = 2;
$k = 1;
while (my $line = <INPUT>){
    chomp($line);

    if ($i eq $.){
        print ">read_".$k." ".$line."\n";
        $i += 4;
    } elsif ($j eq $.){
        print $line."\n";
        $j += 4;
        $k++;
    }

    last if ($k>$n);
}

close INPUT;
```

Simdilik script bu sekilde, neredeyse tamam ancak okuma isimlerini sabit bir sekilde "read_X" seklinde adlandirmaktansa, dinamik bir sekilde, girdi dosyasina gore belirlemek istiyorum. Bunu ileride degistirecegim.
