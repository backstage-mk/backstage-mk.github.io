---
title: Multilayer perceptron (MLP)
author: Mümin Köykıran
date: 2020-01-02 18:32:00 -0500
categories: []
tags: []
---


Çok Katmanlı Algılayıcıyı (MLP) Anlama

![](https://i2.wp.com/miro.medium.com/max/900/1*SHUT1wNHmYZ7CrIppSpnEQ.jpeg?ssl=1)

Yeni yazıma hoş geldiniz. Bu yazıda, Derin Öğrenme Çok Katmanlı Perceptron veya MLP’nin temel Algoritmasından birini tartışacağım.

![](https://i0.wp.com/miro.medium.com/max/727/1*K_zi2aNL0Wx4z19Q0DbxYw.jpeg?ssl=1)

Perceptron Algoritmasının farkındaysanız, perceptron da sadece  **weights**  ile çarpıp  **Bias** ekliyoruz, ancak bunu sadece tek bir katmanda yapıyoruz.

![](https://i2.wp.com/miro.medium.com/proxy/1*S4FYCNkB0eOKR9OrcGu3Mw.jpeg?ssl=1)

Sınıflandırmada bir hata bulduğumuzda veya yanlış sınıflandırılmışsa ağırlığı güncelliyoruz. Ağırlık güncelleme denklemi bu şekilde…

**weight = weight + learning_rate * (expected – predicted) * x**

**ağırlık = ağırlık + öğrenme_orantı * (beklenen – tahmin edilen) * x**

Çok Katmanlı algılayıcıda, birden fazla doğrusal katman (nöron kombinasyonları) olabilir. Üç katmanlı ağın basit örneğini alırsak, ilk katman giriş katmanı ve son katman çıkış katmanı olacak ve orta katman gizli katman olarak adlandırılacaktır. Girdi verilerimizi girdi katmanına besliyor ve çıktıyı çıktı katmanından alıyoruz. Modeli görevimize göre daha karmaşık hale getirmek için gizli katman sayısını istediğimiz kadar artırabiliriz.

![](https://i1.wp.com/miro.medium.com/proxy/1*eloYEyFrblGHVZhU345PJw.jpeg?ssl=1)

İleri Besleme Ağı, en tipik sinir ağı modelidir. Amacı f () işlevine yaklaşmaktır. Örneğin, bir x girişini bir çıkış sınıfı y ile eşleyen bir  **y = f ∗ (x)**  sınıflandırıcısı göz önüne alındığında, MLP, bir eşleme, y = f (x; θ) tanımlayıp öğrenerek bu sınıflandırıcıya en iyi yaklaşımı bulur bunun için en iyi parametreler θ. MLP ağları, birlikte zincirlenen birçok işlevden oluşur. Üç işlevi veya katmanı olan bir ağ f (x) = f (3) (f (2) (f (1) (x))) oluşturur. Bu katmanların her biri, girdilerin doğrusal toplamının afin dönüşümünü gerçekleştiren birimlerden oluşur. Her katman y = f (WxT + b) olarak temsil edilir. F, aktivasyon fonksiyonudur (aşağıda kapsanmıştır), W, katmandaki parametre veya ağırlıklar kümesidir, x, önceki katmanın çıkışı da olabilen giriş vektörüdür ve b, bias vektörüdür. Bir MLP’nin katmanları, tam olarak bağlı birkaç katmandan oluşur çünkü bir katmandaki her birim bir önceki katmandaki tüm birimlere bağlanır. Tamamen bağlı bir katmanda, her birimin parametreleri katmanda bulunan diğer birimlerden bağımsızdır, yani her birimin benzersiz bir ağırlık kümesi vardır.

Denetimli bir sınıflandırma sisteminde, her girdi vektörü bir etiketle veya yer gerçeğiyle ilişkilidir, sınıfını veya sınıf etiketini tanımlayan verilerle verilir. Ağ çıkışı, her giriş için bir sınıf puanı veya tahmini verir. Sınıflandırıcının performansını ölçmek için kayıp işlevi tanımlanır. Öngörülen sınıf gerçek sınıfa karşılık gelmezse kayıp yüksek olacak, aksi takdirde düşük olacaktır. Bazen aşırı takma ve yetersiz takma problemi, modelin eğitimi sırasında ortaya çıkar. Bu durumda, Modelimiz eğitim verileri üzerinde çok iyi performans gösterir, ancak test verileri üzerinde iyi performans göstermez. Ağı eğitmek için bunun için bir optimizasyon prosedürü gereklidir ve kayıp fonksiyonuna ve bir optimize ediciye ihtiyacımız var. Bu prosedür, kayıp fonksiyonunu en aza indiren ağırlık seti W için değerleri bulur.

Popüler bir strateji, ağırlıkları rastgele değerlere başlatmak ve daha düşük bir kayıp elde etmek için bunları tekrarlı olarak iyileştirmektir. Bu arıtma, kayıp fonksiyonunun gradyanı tarafından tanımlanan yönde hareket ettirilerek elde edilir. Ve algoritmanın her yinelemede hareket ettiği miktarı tanımlayan bir öğrenme hızı ayarlamak önemlidir.

### Aktivasyon fonksiyonu:

Doğrusallık olarak da bilinen aktivasyon fonksiyonları, girdi-çıktı ilişkilerini doğrusal olmayan bir şekilde tanımlar. Bu modele keyfi ilişkileri açıklamada daha esnek olma gücü verir. İşte bazı popüler aktivasyon fonksiyonları Sigmoid, Relu ve TanH. Bunları bir sonraki blogumda anlatacağım.

### Modelin Eğitimi

Modelin eğitiminde temel olarak üç adım vardır.

-   Doğrudan geçiş
-   Hata veya kaybı hesapla
-   Geriye doğru geçiş

#### 1. İleri geçiş

Modeli eğitmenin bu adımında, girdiyi modele geçirir ve ağırlıklar ile çarparız ve her katmanda sapma ekler ve modelin hesaplanan çıktısını buluruz.

![](https://i1.wp.com/miro.medium.com/max/723/1*9dByklf9ybdvVtHq6RrOgw.png?ssl=1)

#### 2. Zarar Hesaplama

Veri örneğini (veya bir örneği) geçirdiğimizde, tahmin edilen çıktı (pred_out) olarak adlandırılan modelden bir çıktı alırız ve gerçek çıktı veya beklenen çıktı (Expect_out) olan etikete sahip oluruz. Bunlara dayanarak, backpropagate (Backpropagation algoritması kullanarak) ihtiyacımız olan kaybı hesaplıyoruz. Çıktı ve gereksinimlerimize bağlı olarak kullandığımız çeşitli Kayıp Fonksiyonları vardır.

#### 3. Geriye Geçiş

Kaybı hesapladıktan sonra, kaybı geriye doğru çoğaltırız ve degrade kullanarak modelin ağırlıklarını güncelleriz. Bu, modelin eğitimindeki ana adımdır. Bu adımda, ağırlıklar bu yöndeki gradyan akışına göre ayarlanacaktır.
