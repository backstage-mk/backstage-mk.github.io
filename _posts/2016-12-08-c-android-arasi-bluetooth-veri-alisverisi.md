---
title: "C# Android Arası Bluetooth Veri Alışverişi"
date: "2016-12-08"
categories: 
  - "android"
  - "app-inventor"
  - "csharp"
tags: 
  - "android-arayuzunden-bluetooth-ile-veri-okuma"
  - "android-bluetooth-veri-gonderme"
  - "app-inventor-bluetooth-veri-gonderme"
  - "bluetooth-ile-android-c-komut-gonderme"
  - "bluetooth-ile-c-android-arasi-iletisim"
  - "c-arayuzunden-bluetooth-ile-veri-okuma"
  - "c-bluetooth-veri-gonderme"
  - "c-programina-bluetooth-ile-veri-gonderme"
image:
  src: "/asset/c-android-arasi-bluetooth-veri-alisverisi/C-Android-Arasi-Bluetooth-Veri-Alisverisi-C-Arayuzu.png"
---

Merhabalar bu benim sizler için hazırladığım ilk yazım. Öncelikle olayın biraz hikayesini anlatayım diyorum, üzerinde çalıştığım bir projede C# programıma Bluetooth ile text göndermem gerekiyordu bende hemen araştırmaya koyuldum gerekli bilgili edindikten sonra C# programımda gerekli düzenlemeyi yaptım fakat işin android kısmında sadece text gönderme olsa Java ile programı yazayım fakat ses tanıma vb. bazı işlemler yapmam gerekiyordu bende Java ile kodlamak yerine ai2.appinventor.mit.edu ile işime yarayacak bir program hazırladım iki programda istediğim şekilde çalıştı bu arada şuan detay vermiyorum fakat ilerleyen zamanlarda üzerinde çalıştığım proje hakkında ilerlemelerimi blogum da paylaşacağım. Buraya kadar işin hikayesi şimdi olayın çalışma mantığına geçelim bu arada test etmeniz için örnek hazırladığım C# dosyalarını ve App İnventor dosyalarını paylaşacağım import edip kullanabilirsiniz.

**C# Arayüzü Aşağıdaki gibidir;**

![C-Android-Arasi-Bluetooth-Veri-Alisverisi-C-Arayuzu](/asset/c-android-arasi-bluetooth-veri-alisverisi/C-Android-Arasi-Bluetooth-Veri-Alisverisi-C-Arayuzu.png)


Yukarıda gördüğünüz GerekenleriGetir Buttonuna tıklayınca bilgisayardaki açık serial portları, veri gönderme hızlarını, stop bits, parity, data bits değerlerini combobox içlerine yerleştirip varsayılan en uygun değerleri seçecektir daha sonrasında bağlan buttonuna tıklıyoruz sonra aşağıda görseli bulunan android programından ilerleyeceğiz

**Android Program Arayüzü:**

![C-Android-Arasi-Bluetooth-Veri-Alisverisi-Android-Arayuzu](/asset/c-android-arasi-bluetooth-veri-alisverisi/C-Android-Arasi-Bluetooth-Veri-Alisverisi-Android-Arayuzu.png)

Android kısmında ise önce ayarlardan bluetooth açıyoruz ve bilgisayarımız ile bağlıyoruz bu kısmı her kullanmadan önce yapmıyoruz sadece telefonun bilgisayardaki bluetooth ismini tanıması için yapıyoruz fakat her seferinde kullanmadan önce bluetooth ayarımızı açmamız gerek sonuçta BT ile veri göndereceğiz neyse daha sonra programa geri dönüp Bağlan buttonuna tıklıyoruz açılan kısımdan daha önce bağlantı kurulmuş bilgisayarımızı seçiyoruz eğer bir bağlantı sorunu olmazsa durum kısmında bağlandı yazacaktır sonrasında C# ve Android arasında veri gönderip alabilirsiniz.

**App İnventor Block Arayüzü:**

![C-Android-Arasi-Bluetooth-Veri-Alisverisi-App-Inventor-Blok](/asset/c-android-arasi-bluetooth-veri-alisverisi/C-Android-Arasi-Bluetooth-Veri-Alisverisi-App-Inventor-Blok.png)

C# Projesi ve kodları [**Github Profilim**](https://github.com/muminkoykiran/bluetooth_data_exchange){:target="_blank"} üzerinden indirebilirsiniz.

APK dosyasını [**Buradan**](/asset/c-android-arasi-bluetooth-veri-alisverisi/CsharpAndroidArasiBluetoothVeriAlisverisi-apk.zip){:target="_blank"} indirebilirsiniz.

App İnvetor üzerinde import etmek için .aia dosyasını [**Buradan**](/asset/c-android-arasi-bluetooth-veri-alisverisi/CsharpAndroidArasiBluetoothVeriAlisverisi-aia.zip){:target="_blank"} indirebilirsiniz

Ayrıca C# kısmı daha başka projelerinizde arduino, raspberry pi veya herhangi bluetooth destekli mikro denetleyicilerde iletişim için kullanabilirsiniz kendinizde geliştirip sanal asistanlar, robotlar, akıllı ev sistemleri, giyilebilir sistemler yapabilirsiniz. Yaptığınız projeleri bilgisayardan kontrol edebilirsiniz.
