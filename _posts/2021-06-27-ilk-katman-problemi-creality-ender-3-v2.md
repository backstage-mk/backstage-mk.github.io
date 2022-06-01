---
title: "İlk Katman Problemi - Creality Ender 3 v2"
author: Mümin Köykıran
date: "2021-06-27"
categories: 
  - "3d yazici"
  - "creality ender 3 v2"
tags: 
  - "ilk katman problemi nasıl düzeltilir"
  - "tabla sallanma sorunu çözümü"
  - "cura üzerinden ilk katman sorunu çözümü"
  - "ender 3 v2 first layer not sticking"
  - "ender 3 v2 ilk katman yapışmıyor"
image:
  src: /asset/ilk-katman-problemi-creality-ender-3-v2/ender-3-v2-ilk-katman-yapismiyor.jpg
---

Merhaba, bildiğiniz gibi geçtiğimiz günlerde **[3D yazıcı](/categories/3d-yazici/)** dünyasına giriş yapmıştım. Kullanmakta olduğum **[Creality Ender 3 v2](/categories/creality-ender-3-v2/)** model yazıcımın tüm konfigürasyonlarını içerisinde yer alan videoya ve internet üzerinden elde ettiğim araştırmalara göre sağladım. Belirli kullanım sonrası bazı yerlerde daha ilk katman basımı sırasında bazı noktaların incelmeleri, baskıların havada kalması, ilk baskının yapışmamaları gibi sorunlar ile karşılaştım ve bu yazımda sizelere bu sorunların çözümleri sırasında izlediğim yollardan bahsedeceğim.

Bu anlattıklarımdan sonra tabi ilk olarak aklınıza geldiği gibi neden bazı kullanımlarda bu sorun ile karşılaşıyoruz? Aslına bakarsanız farklı farklı alınan baskılar tabla üzerinden farklı noktalardan baskıya başlamaktadır. Bu durumda eğer tabla ayarınız stabil değil ise bu gibi sorunlar ile karşılaşılması normaldir. Ben kendimde tüm ayarlamaları doğru yaptığıma emin olduğum halde hala bazı baskılarda sorun yaşamama anlam verememiştim. Sonra kalibre işlemi sırasında anladım ki o an kalibre doğru dahi olsa ısı etkisi ile tellerin genleşmesi, üzerine baskı sırasında ortaya çıkan ağırlığın kalibreyi etkilemesi vb. sorunlar çıkmaktaydı. Normal şartlarda baskı sırasındaki ağırlık ne kadar etki edebilir ki dersiniz... Eğer yazıcınızı tabla (BED) kısmı sallanıyor ise işte bu büyük bir probleme neden olmaktadır. Zaten bunu anlayınca çözüm için _%98_'lik kısım tamamlanmış oluyor :)


## 3D Yazıcılarda Tabla Sallanma Sorunun Çözümü

Tabla sallanma sorunu, yazının eksenlerinin hareketi sırasında mikron düzeyinde tablaya olan yaklaşma ve uzaklaşmalar filamentin çıkış yoğunluk ve hızının tüm bölgelere eşit miktarda olmamasına sebep olmaktadır. Aslında bu sorunu düzeltmek çok büyük ölçüde güzel baskılar almanıza olanacak sağlayacaktır.

Benim bu işlemlemler sırasında izlediğim video aşağıdaki gibidir.

{% youtube 5no5XcOzAHY %}


**[Video Linki](https://www.youtube.com/watch?v=5no5XcOzAHY)**


Ayrıca video içerisinde 3D yazıcınızın performansını arttırmya yönelik bazı baskı ürünleri de yer almaktadır. Dilerseniz onlarıda daha detaylı araştırabilir ve kullanımınıza sunabilirsiz. Eğer benim bu baskıları öncesinde denememi isterseniz yorumlarda belirtmeyi unutmayın.


## Baskı Yüzeyi Kalitesini Arttırmak

Aşağıdaki videoda yer alan adımları takip ederseniz yazılımsal veya kalibre ayarı dışında tabla üzerinden yapılması gereken çalışmaların yer aldığını göreceksiniz.

{% youtube uOK2LVOeNuE %}


**[Video Linki](https://www.youtube.com/watch?v=uOK2LVOeNuE)**

## İlk Katman Üzerine Bilgilendirici Bir Video

{% youtube 47CkITEiSNQ %}


**[Video Linki](https://www.youtube.com/watch?v=47CkITEiSNQ)**


## Cura Üzerinden Konfigürasyonlar ile İlk Katman Sorunu Çözümü

Buraya kadar olan aşamaların hepsini yaptığın ve tüm fiziksel iyileştirmlere rağmen hala istediğiniz kalitede ve düzgünlükte ilk katmanı elde edemiyorsanız aşağıdaki video ile kesin bir çözüm elde edebileceksiniz. Bu videoda cura yazılımı üzerinde ilk katmanda malzeme yoğunluğu, akışkanlık hızı, ilk katmanda tabla sıcaklığı, ilk katmanda filament sıcaklık ve yoğunluklarını değiştirerek, ortama uygun koşulları sağlayarak düzgün bir farkı elde edbeiliyoruz.


{% youtube V6cYJQ-l5Ds %}


**[Video Linki](https://www.youtube.com/watch?v=V6cYJQ-l5Ds)**