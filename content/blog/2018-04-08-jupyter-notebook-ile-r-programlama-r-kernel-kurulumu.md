---
author: Güngör Budak
date: '2018-04-08T14:00:00+03:00'
slug: jupyter-notebook-ile-r-programlama-r-kernel-kurulumu
tags:
- jupyter
- notebook
- r
- r programlama
- r kernel
- irkernel
- kurulum
- corrplot
- korelasyon
- korelasyon analizi
- korelasyon grafiği
title: Jupyter Notebook ile R Programlama - R Kernel Kurulumu
year: '2018'
---

Daha önceki bir yazımda [Jupyter'in kurulumundan ve Jupyter Notebook]({% post_url 2018-03-31-jupyter-python-nedir-nasil-kurulur %})'tan bahsetmiştim. Jupyter'in kurulumu Jupyter Notebook'a Python kernelini direkt kuruyor ve Python ile programlamayı mümkün kılıyor ancak biyoenformatikte sıkça kullanılacak bir diğer programlama dili olan R programlama için ilgili kerneli ekstra kurmak gerekiyor. Bu yazımda bu kernelin kurulumundan bahsedeceğim.

Öncelikle [Jupyter kurulumu]({% post_url 2018-03-31-jupyter-python-nedir-nasil-kurulur %}) ve [R kurulumu](https://cran.r-project.org/) yapılmış olması gerekiyor.

Daha sonra Terminal'den aşağıdaki komutu kullanarak bir R oturumu başlatın:

```
Gungors-MacBook-Pro:~ gungor$ R

R version 3.4.3 (2017-11-30) -- "Kite-Eating Tree"
Copyright (C) 2017 The R Foundation for Statistical Computing
Platform: x86_64-apple-darwin17.3.0 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

>
```

[![R](/public/images/jupyter-notebook-r-kernel-1.png)](/public/images/jupyter-notebook-r-kernel-1.png)

Aşağıda gösterildiği gibi gerekli R paketlerini kurun:

```R
> install.packages(c('repr', 'IRdisplay', 'evaluate', 'crayon', 'pbdZMQ', 'devtools', 'uuid', 'digest'))
```

`devtools` kullanarak IRkernel'i GitHub kaynağından kurun:

```R
> devtools::install_github('IRkernel/IRkernel')
```

Ve son olarak da R kerneli tanımlayın:

```R
> IRkernel::installspec()
```

Bu `ir` koduyla, `R` adında bir kerneli Jupyter'e ekleyecek. Bunları değiştirmek için tanımlarken aşağıdaki gibi ayarlamalar yapabilirsiniz (örneğin özel bir versiyon için):

```R
> IRkernel::installspec(name = 'ir34', displayname = 'R 3.4')
```

Jupyter Notebook'u başlattığınızda `New` butonundan `R 3.4` kernelini seçerek Jupyter Notebook üzerinde R programlamaya başlayabilirsiniz.

[![R notebook](/public/images/jupyter-notebook-r-kernel-2.png)](/public/images/jupyter-notebook-r-kernel-2.png)

Küçük bir analiz ile bir test yapabiliriz. Bu analizi [korelasyon grafiği çıkarma üzerine bir makale](http://www.sthda.com/english/wiki/visualize-correlation-matrix-using-correlogram)den aldım. Makalede de görülebileceği gibi aşağıdaki kodları sırası ile çalıştırıyor olacağım.

```R
# corrplot paketini kur
install.packages("corrplot")

# corrplot paketini yükle
library("corrplot")

# araçlar verisinin ilk satırlarını gör
head(mtcars)

# korelasyon analizi yap ve sonucun ilk satırlarını gör
M <- cor(mtcars)
head(round(M, 2))

# korelasyon grafiği çizdir
corrplot(M, method="color")
```

Öncelikle `Desktop`'ta yeni bir klasör açalım ve Terminal'den bu klasöre gidelim (bu komutlar Linux tabanlı işletim sistemleri / macOS için geçerlidir, Windows için de benzer işlemler farklı komutlarla yapılmalıdır):

```bash
Gungors-MacBook-Pro:~ gungor$ cd ~/Desktop/
Gungors-MacBook-Pro:Desktop gungor$ mkdir playground
Gungors-MacBook-Pro:Desktop gungor$ cd playground/
Gungors-MacBook-Pro:playground gungor$ 
```

Jupyter Notebook'u başlatalım (bu komut tarayıcınızda yukarıdaki resimdekine benzer yeni bir sekme başlatacak):

```bash
Gungors-MacBook-Pro:playground gungor$ jupyter notebook
```

Açılan sayfada `New` menüsünden `R 3.4` notebook'unu seçip (yukarıdaki resimde göründüğü gibi) yeni bir notebook açalım.

[![Yeni R notebook](/public/images/jupyter-notebook-r-kernel-3.png)](/public/images/jupyter-notebook-r-kernel-3.png)

Bu notebook'ta istediğimiz R komutunu/kodunu çalıştırabiliriz; yeni R paketleri kurabilir, mevcut R paketlerini yükleyebilir, analizler yapıp grafikler oluşturabiliriz.

Jupyter Notebook'ta gri arkaplanlı hücrelerde Markdown ile stillenebilir yazılar ve kodlar bulunabilir. Bir hücrenin tipi hücre seçildikten sonra üst menüdeki `Cell` sonrasında `Cell Type` menüsünden ayarlanabilir.

Hücreler doldurulduktan sonra üst menünün altındaki menüde bulunan play simgeli buton ile çalıştırılabilir, gene bu menüdeki `+` simgesi ile yeni hücre oluşturulabilir. Bir hücre çalıştırılırken sol tarafındaki `In [ ]:` kısmı, `In [*]:` olarak gösterilecek ve bittiğinde de sırasına göre bir numara ile gösterilecektir, örneğin `In [1]:`. Çalıştırıldıktan sonra hemen altında varsa çıktısı görünecektir.

[![R notebook analiz](/public/images/jupyter-notebook-r-kernel-4.png)](/public/images/jupyter-notebook-r-kernel-4.png)

Tüm hücreler çalıştırıldığında ise aşağıdaki gibi bir korelasyon grafiği bu veri için gösterilecektir.

[![R notebook analiz sonuç](/public/images/jupyter-notebook-r-kernel-5.png)](/public/images/jupyter-notebook-r-kernel-5.png)
