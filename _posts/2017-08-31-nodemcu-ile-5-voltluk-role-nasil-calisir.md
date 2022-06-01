---
title: "NodeMCU ile 5 voltluk röle nasıl çalışır?"
date: "2017-08-31"
categories: 
  - "Projeler"
  - "NodeMCU"
tags: 
  - "rölenin ışıkları yanıyor ama tık sesi çıkmıyor"
  - "nodemcu"
  - "role"
  - "reley"
image:
   src: "/asset/nodemcu-ile-5-voltluk-role-nasil-calisir/nodemcu-reley.jpg"
---

Merhabalar, yapmış olduğum akıllı priz de geçtiğimiz hafta bir sorun ile karşılaştım bu sorunu kısaca değinip nasıl çözdüğümüzü sizler ile paylaşacağım.

NodeMCU, 2′li 5V Röle Kartı, 3'lü Yonca Topraklı Priz ve Micro USB 5V çıkışa sahip standart bir şarj aleti kullanarak kendi akıllı prizimi oluşturdum, kontrolünü ise yazdığım android uygulama veya kendi kodlamış olduğum sanal asistan ile yapıyorum, sözler ile evdeki ışığı ve prize bağlı eşyaları açıp kapatmak hoş oluyor :)

Sonraki yazılarda Sanal Asistanımın özelliklerinin tanımlarını yavaş yavaş yapmayı düşünüyorum ayrıca Akıllı Prizimin de kullanım halindeki videoları paylaşacağım. Kısa bilgilendirmeden sonra sorunuma gelelim.

Arduino ve ESP8266 tabanlı olan NodeMCU geliştirme kartı 3.3V GPIO sahiptir bu sebeple 5 volt ile tetiklenen röle kullanamamamız lazım fakat ilk prizi topladıktan sonra sorunsuz çalışıyordu ve üzerine taktığım fişleri sorunsuz aç/kapat yapıyordu sonrasında o sırada elimde tek NodeMCU olduğu için diğer denemelerimi yapmak için akıllı prizden çıkartıp başka çalışmalar yaptım işim bitince eskisi gibi diğer kodları yükledim ve yerine koydum, ses ile röle 1 ve röle 2'yi aç kapat yapıyordum ama sadece rölenin ışıkları kapanıp sönüyordu o bir röle içindeki tik sesi çıkmıyordu bu arada tik seni nereden geliyor ona da kısaca değineyim;

> Röle 5V ile tetiklendiği zaman rölenin bobini enerjilenir, bobin elektron mıknatısı görevi görerek rölenin içinde yer alan metal parçayı çekerek iki parçanın temas etmesini sağlar. Bu şekilde devrede bulunan elektrikli cihazlar örneğin fan, lamba, motor, ısıtıcı vb.  çalışır ve kapanır. Bobinin enerjisi kesildiğinde hareketli parçaya bağlı olan bir yay parçayı tekrar eski konumuna getirir.

![](/asset/{{page.id | replace:'/posts/',''}}/2-way-5v-relay-module.png)
*2 way 5v relay module*

**Rölenin ışıkları yanıyordu ama tık sesi çıkmıyor**du bende hemen prizini içini açtım, rölenin bağlantılarını, prizin bağlantıları ve kodları kontrol ettim ama bir sorun yoktu fakat sinyali gönderdikten sonra tornavida ile rölenin üzerine tıklatınca tetikleme başlıyordu sonra aklıma voltaj olayı geldi ilk kullandığımda 3.3 V ile tetikleniyordu bunu internette araştırdım aynı sorun ile başkasına karşılaşmış ama o yanlışlıkla 12V Röle almış onu 5 V ile tetiklemeyi denemiş tabi ışıkları yanıyor ama röle içinde tık sesi yokmuş bu kişi sonra röle kartından röleyi başka bir röle ile değiştiriyor sorun çözülüyor benim parçalar yeni olduğu için ve daha önce kullandığım için sorun yoktu sonrasında belki ışıklar yanıyor ama röle tetiklenmesi için güç yetmiyordur dedim görselde üzerinde iki pini bağlayan mavi renkteki parçayı çıkartıp JD-VCC pinine 3.3 V ve onun sırasında bulunan diğer GND pinine de NodeMCU üzerinden GND bağlantısını yapınca sorunsuz çalıştı.

![](/asset/{{page.id | replace:'/posts/',''}}/nodemcu_pinout.png)
*Nodemcu Pinout*
