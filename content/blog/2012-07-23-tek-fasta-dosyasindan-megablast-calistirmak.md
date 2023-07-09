---
author: Güngör Budak
date: '2012-07-23T05:49:00.002+03:00'
slug: tek-fasta-dosyasindan-megablast-calistirmak
tags:
- regular expressions
- perl
- düzenli ifadeler
- megablast
- fasta
- fastq
title: Tek FASTA Dosyasindan MegaBLAST'i Calistirmak - Duzenli Ifadeler
year: '2012'
---

Asagida MegaBLAST'i FASTA dosyasi okuyarak calistirmak ve sonuclari bir dizinde toplayabilmek amaciyla yazdigim Perl scripti ve onun aciklamasi var. Bu script tasarlamakta oldugum pipeline'in onemli bir parcasi. Bu script ilk yazdigim olan ve sadece bir FASTA dosyasi uzerinden tum okumalara ulasabilen script.

```perl
#!user/local/bin/perl
$database = $ARGV[0];
$fasta = $ARGV[1]; #input file
$sp = $ARGV[2]; #starting point
$n = $ARGV[3] + $sp;

if(!defined($n)){$n=12;} #set default number

open FASTA, $fasta or die $!;

while (my $line = <FASTA>){
    chomp $line;

    if ($line =~ /^>(\w+$sp)\s/){

        $name = $1;
        $input = $fasta."[".$name."]";

        system("megablast $input $database -OUTFILE=megablast/$name.megablast -nobatch -d");

        $sp++;
        last if ($sp == $n);
    }
}

close FASTA;
```

En son MegaBLAST yapabilmek icin sadece eslesemeyen okumalara sahip FASTQ dosyasini FASTA formatina cevirmistim. Simdi, bu FASTA dosyasiyla cesitli veritabanlarinda okumalari arayacagim ve cikti dosyalarini saklayacagim. Daha sonra da bu dosyalari inceleyecegim (parsing).

Bu projedeki FASTA dosyasi bir insan genomuna ait, bu yuzden oldukca buyuk bir dosya. Daha onceki yazilarimda toplamda yaklasik 5.5 milyon okumanin (ya da dizinin) oldugunu soylemistim. Ayrica dizilemeyi yapan makinenin ve dizileme islemleri genel olarak goz onunde bulunduruldugunda, deneme icin tum bu okumalarin MegaBLAST ile aratilmasi pratik degil. Bu yuzden bir kismini, ama gene de buyuk bir kismini ele alacagim. Ise yarar diyebilecegimiz kismi, dosyanin ortalarindaki okumalar olabilir. Bu okumalar digerlerine gore, daha kaliteli bir sekilde dizileniyor ve kaydediliyor. Bu yuzden ben de aramaya ortalardan baslayacak bir script yazdim. Scripte parametre olarak kacinci okumadan baslamasi gerektigini ve o okumadan itibaren o arama icin kac okuma aramasini istedigimizi ekledim. Elbette veritabani ismi, FASTA dosyasi ismi, her durumda olmasi gereken parametreler.

MegaBLAST arama scriptinde okuma adlarini duzenli ifadeler (regular expressions) kullanarak aliyorum, cunku eger gercekten herkes tarafindan kullanilabilecek bir pipeline tasarlamak istiyorsam, duzenli ifadeleri kullanmam sart. Ayrica, ismi aratirken, parametreden aldigim sayiyi da kullaniyorum. Kullanici scripte parametre olarak hangi okumadan baslamasi gerektigini belirttigi icin, okuma adlarini alirken o sayili okumayi bulup, devam etmem gerekiyor.

Ornegin eger okuma isimleri ">read_1", ">read_345", ">read_3000000" diye gidiyorsa, buyuktur isareti, birkac karekter veya alt cizgi ve bir degiskende saklanan okuma sayisini eslestirerek okuma adini buluyorum. Perl'de ise bunu, bir kontrol yapisi icinde soyle gosteriyoruz.

```perl
if ($line =~ /^>(\w+$sp)\s/){

}
```

Yukaridaki blokta $line degiskeni, while dongusu ile okuyor oldugum satira denk geliyor ve "=~" operatoruyle bu satirdaki baslagictan itibaren ">" karakterini direkt, sonra "read_" ifadesini "(\w+)" ile, okuma sayisini gene direkt "$sp" degiskeni ile karsilastiriyorum ve sonra da "\s" ile sonunda bir bosluk (space) karakteri oldugunu belirtiyorum. Hatirlayacak olursaniz, FASTA dosyasini olustururken, ismin sonunda bir bosluk birakip, daha sonra FASTQ dosyasindan gelen basligi ayni satira eklemistim. Bu ifade aciklamam gereken diger karakter ise "^". Bu karakterle, satirin basindan itibaren karsilastirmak istediginizi belirtiyorsunuz. Elbette duzenli ifadelerde olmasi gereken "/ ifade /" kurali gecerli ve buna uyuyorum. 

Duzenli ifadelerle bu tarz karsilastirma yapmanin bircok yolu var. Bunlari baska bir yaziyla ya da yazi dizisiyle paylasmak istiyorum.

```perl
system("blastplus -programname=megablast $input $database -OUTFILE=megablast/$name.megablast -nofilter -nobatch -d");
```

Devaminda system komutu ile megablasti calistiriyorum. Ek olarak kullandigim parametreler, "-nofilter" (tekrar eden dizileri maskelemesin diye) ve "-nobatch".

Bu script bize her okumanin arama sonuclarini ayri .megablast dosyasi olarak veriyor ve onlar uzerinden inceleme yapabiliyoruz.
