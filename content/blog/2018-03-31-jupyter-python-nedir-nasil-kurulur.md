---
author: Güngör Budak
date: '2018-03-31T19:42:00+03:00'
slug: jupyter-python-nedir-nasil-kurulur
tags:
- python
- ipython
- jupyter
- notebook
- anaconda
- kurulum
title: Jupyter / Python Nedir, Nasıl Kurulur?
year: '2018'
---

Jupyter çeşitli programlama dilleri için etkileşimli bir ortam sağlayan yazılımdır. Orijinal olarak IPython (interactive python) adıyla, Python programlama dili için geliştirildi ancak daha sonra kurucuları Jupyter projesini başlatıp IPython'ın birçok tarafını Jupyter'e kaydırdı. IPython, sadece Jupyter'in kerneli olarak devam ediyor.

Jupyter'in özellikleri;

- Etkileşimli bir shell sunması, Komut İstemi/Terminal'den `jupyter console` komutu ile başlatılır ve orijinal Python shell'ine göre otomatik tamamlama gibi kullanıcı dostu özellikleri barındırır.
- Tarayıcı tabanlı defter (notebook) sunması, Komut İstemi/Terminal'den `jupyter notebook` komutu ile başlatılır, açılan tarayıcı penceresinden yeni defter oluşturularak çeşitli programlama dillerinde kodlar yazılabilir ve bu kodlar çalıştırılarak çıktıları (metin, grafik, vs) etkileşimli olarak direkt tarayıcıda görüntülenebilir. Bu özelliği ile programlama dili öğretmek ya da bir programlama dilinde kod çalıştırıp sonuçlarını analiz etmek çok pratikleşir.
- Paralel hesaplama için araçlar barındırır.

Jupyter sadece Python ile değil, R, Julia, Ruby, ve Haskell gibi programlama dilleri ile de kullanılabilir. Bu programlama dilleri için ekstra yüklemeler yapılmalıdır.

**Jupyter Nasıl Kurulur?**

Öncelikle, sisteminizde Python 3.3 ya da yukarısı ya da Python 2.7 kurulu olmalıdır. İşletim sistemine (Windows, macOS ya da Linux) göre değişecek olsa da, Python kurulumu için, [Python'ın web sitesindeki Downloads bölümü](https://www.python.org/downloads/)nden indirilecek kurulum paketi çalıştırılarak, adım adım yönergeler takip edilmeli ve uygulanmalıdır. Python 3 mü yoksa 2 mi sorusunun yanıtı ise, Python 3 olmalıdır, çünkü yakında Python 2 daha fazla desteklenmeyecek ve Python 3 devam edecektir.

Jupyter'i Anaconda aracılığıyla kurabilirsiniz. Anaconda, birçok veri bilimi ile ilgili paketi ve Python'ın kendisini barındıran bir süperpakettir. Yani, bu yazılımı kurduğunuzda Jupyter dahil birçok birbirinden faydalı paket de sisteminize kurulacaktır. Python versiyonu için olduğu gibi Anaconda için de [Downloads bölümü](https://www.anaconda.com/download)nden versiyon 3 seçilmelidir. Eğer bu yolu seçtiyseniz yukarıdaki Python kurulumu atlayabilirsiniz.

[![Anaconda](/public/images/jupyter-kurulum-1.png)](/public/images/jupyter-kurulum-1.png)

Örneğin Anaconda, Windows için yukarıdaki resimde bulunan sağdaki yeşil buton yardımıyla indirilecek dosya ile kurulabilir. Diğer sistemler için de kurulum seçenekleri aynı sayfada bulunmaktadır.

Anaconda aracılığıyla kurulmaması durumda, Python Package Index aracı `pip` ile de kurabilirsiniz. Tabii, öncelikle `pip`'i kurmanız gerekecek, bunu için;

[get-pip.py dosyasını indirmek için bu bağlantıya sağ tıklayın](https://bootstrap.pypa.io/get-pip.py) ve kaydedin. Daha sonra Komut İstemi/Terminal'den ilgili klasöre gidin ve aşağıdaki komutu çalıştırın;

```bash
python get-pip.py
```

[Bu kurulum ile ilgili original belge için tıklayın](https://pip.pypa.io/en/stable/installing/).

Son olarak da, Jupyter'i yüklemek için aşağıdaki komutu çalıştırın;

```bash
python -m pip install jupyter
```

[Bu kurulum ile ilgili original belge için tıklayın](http://jupyter.org/install).

Jupyter Notebook'u (Defter) çalıştırmak için Komut İstemi/Terminal'den aşağıdaki komutu çalıştırabilirsiniz;

```bash
jupyter notebook
```

[![Jupyter Notebook](/public/images/jupyter-kurulum-2.png)](/public/images/jupyter-kurulum-2.png)

Yukarıdaki komut ile birlikte default tarayıcıda bu sayfa açılacak ve buradan yeni notebook'lar oluşturabileceksiniz. Bunun için yukarıdaki resimdeki gibi sağ üstteki `New` butonuna tıklayın ve `Notebooks` altından istediğiniz programlama dilini seçin.
