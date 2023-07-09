---
author: Güngör Budak
date: '2012-08-09T09:15:00.000+03:00'
slug: srsde-coklu-arama-yapmak
tags:
- getz
- organizma
- hash
- perl
- pipe
- array
- megablast
- string
- srs
title: SRS'de Coklu Arama Yapmak
year: '2012'
---

Inceleme yapan scriptin en son hali, oncekilere gore daha fazla okuma inceliyor oldugu icin her okuma icin SRS uzerinde isim aramak oldukca zaman alan bir islemdi. Oyle ki, son inceleme 4 gun surdu.

Bunu azaltmak icin inceleme scriptini tamamen degistirdim. Oncelikle her zaman oldugu gibi esik degerini gecenleri aliyor ama direkt bunlarin ID numaralarini bir dizide (array) listeliyorum. Daha sonra bu listenin herbir elemanini boru karakteri ile ayirarak bir string haline getiriyorum. Son olarak bu stringi direkt getz komutuyla SRS'de aratip, tek seferde tum sayfada esik degerini gecen organizmalarin isimlerini alip, bunlari tek tek okuyup ayirarak hash icinde sakliyorum.


```perl
while (@params = $blast_obj->next_alignment(fields => ['name', 'identity', 'overlap'])) {
        $overlap_seen = $params[2];
        $mismatch_seen = $params[2] - $params[1];

        if ($overlap_seen >= $overlap_threshold and $mismatch_seen <= $mismatch_threshold) {
            if ($database eq "refseq_dna") {
                $params[0] =~ /:([A-Z|0-9]*\_[A-Z|0-9]*)/;
                push(@names, $1);
            }
        }
    }

    $ids = join("|", @names);

    if ( !($ids eq "") ) {
        open (PIPE, "getz '[$database:$ids]' -vf 'ORGANISM' |") or die $!;
        while(my $line = <PIPE>) {
            $line =~ /\t(.*)/;
            $organism_names{$1}++;
        }
    }
    close PIPE;
```

Gene her ID numarasini duzenli ifade ile elde edip, bunu @names dizisine push komutu ile ekliyorum. Bu tumu icin bittiginde liste elemanlarini join komutu ile aralarinda "\|" karakteri olacak sekilde birlestirip $ids stringini elde ediyorum. Sonra eger bu string bos degilse getz komutuyla arama yapip, elde ettigim cok satirli ciktiyi [ozel bir sekilde okuyup]({% post_url 2012-07-23-unixte-perl-ile-bir-komut-ciktisini-okumak %}) her organizma ismini %organism_names hashine key olarak ekliyorum.
