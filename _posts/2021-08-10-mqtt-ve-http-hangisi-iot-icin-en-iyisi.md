---
title: "MQTT ve HTTP: Hangisi IoT için en iyisi?"
author: Mümin Köykıran
date: "2021-08-10"
categories: 
  - "IoT"
  - "MQTT"
  - "Web"
tags: 
  - "MQTT VS HTTP"
image:
  src: /asset/mqtt-ve-http-hangisi-iot-icin-en-iyisi/mqtt_vs_http.jpeg
---

IoT dünyasına yaklaşırken, IoT cihazlarını iletmek için kaç protokol kullanabileceğimiz merak edilebilir.

AMQP, CoAP, MQTT ve omnipresence HTTP gibi birçok protokol vardır.

Pratik dünyada kalmaya çalışarak ikisini kısaca karşılaştırabiliriz: MQTT ve HTTP

MQTT protokolü, makineden makineye (M2M) ve IoT bağlantı protokolü olarak tasarlanmıştır.

HTTP en popüler ve yaygın olarak kullanılan protokoldür. Ancak son yıllarda MQTT hızla çekiş kazanıyor. IoT geliştirmeden bahsederken geliştiriciler aralarında seçim yapmak zorundadır.

**MQTT** , **Message Queuing Telemetri Aktarımı** anlamına gelir **.**

Bu protokol bu nedenle hafiftir ve genellikle en küçük ölçüm ve izleme cihazlarının bazıları tarafından desteklenir ve bazen kesintili ağlara ulaşan yol üzerinden bilgi iletebilir. daha fazlasını okumak için basit MQTT protokol mimarisi (broker tabanlı) burada

HTTP, **Köprü Metni Aktarım Protokolü** anlamına gelir ; çoğumuz bunu biliyoruz, istemci (web kullanıcısı) ve web sunucusu arasındaki HTTP bağlantısı.

İnternet için yaygın olarak kullanılan protokoldür, çok fazla veri yayınlaması gereken IoT cihazları için en çok kullanılan protokol olabilir. Paketlerin yönlendirilmesi için normal IP başlığını kullanır ve veriler iletilmeden önce şifrelenmez.

## Tasarım ve Mesajlaşma

MQTT veri merkezlidir, HTTP ise belge merkezlidir. HTTP, istemci-sunucu bilgi işlemi için istek-yanıt protokolüdür ve her zaman mobil cihazlar için optimize edilmez. MQTT’nin bu terimlerdeki temel faydaları, hafifliği (MQTT verileri bir bayt dizisi olarak aktarır) ve kaynakları kısıtlı cihazlar için mükemmel kılan ve pil tasarrufuna yardımcı olan publish/subscribe olma modelidir.

Ayrıca publish/subscribe modeli, müşterilere birbirinden bağımsız bir varlık sağlar ve tüm sistemin güvenilirliğini artırır. Bir istemci arızalandığında, tüm sistem düzgün çalışmaya devam edebilir.

## Hız ve Teslimat

3G ağlarındaki ölçümlere göre, MQTT’nin çıktısı HTTP’lerden 93 kat daha hızlıdır.

Ayrıca, HTTP ile karşılaştırıldığında MQTT Protokolü yüksek teslimat garantileri sağlar. Hizmet Kalitesinin 3 düzeyi vardır:

– en fazla bir kere: en iyi çabayla teslimatı garanti eder.

– en az bir kez: bir mesajın en az bir kez teslim edileceği garanti edilir. Ancak mesaj birden fazla kez iletilebilir.

– tam olarak bir kez: her mesajın karşı taraf tarafından yalnızca bir kez alınmasını garanti eder

MQTT ayrıca kullanıcılara Son vasiyet ve Ahit ve Saklanan mesajlar seçenekleri sunar. Birincisi, bir istemcinin beklenmedik bir şekilde bağlantısının kesilmesi durumunda, abone olan tüm istemcilerin bir aracıdan bir mesaj alacağı anlamına gelir. Tutulan mesaj, yeni abone olunan bir müşterinin anında durum güncellemesi alacağı anlamına gelir.

HTTP Protokolü bu yeteneklerin hiçbirine sahip değildir.

## Karmaşıklık ve Mesaj Boyutu

MQTT oldukça kısa bir spesifikasyona sahiptir. Geliştiriciler için önemli olan yalnızca BAĞLAN, YAYINLA, ABONE OLUN, ABONELİKTEN KALDIR ve BAĞLANTIYI KESİN türleri vardır. Oysa HTTP özellikleri çok daha uzundur.

MQTT çok kısa bir mesaj başlığına ve 2 baytlık en küçük paket mesaj boyutuna sahiptir. HTTP protokolü ile metin mesajı formatının kullanılması, uzun başlıklar ve mesajlar oluşturmasına izin verir. İnsanlar tarafından okunabildiği için sıkıntıların giderilmesine yardımcı olur, ancak aynı zamanda kaynak kısıtlı cihazlar için gereksizdir.

## Çözüm

MQTT Protokolü kullanımı kolaydır. Gelecekteki çözümler için yanıt süresi, verim, daha düşük pil ve bant genişliği kullanımı ilk sırada olduğunda önemlidir. Aralıklı bağlantı durumunda da mükemmeldir.

HTTP değerli ve genişletilebilir. Ancak MQTT, IoT geliştirme denildiğinde daha uygundur.

## MQTT ve HTTP protokolleri arasında karşılaştırma
  

| Özellikleri          | MQTT                                                                                                                                                                | HTTP                                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Tam form             | Mesaj Kuyruğu Telemetri Aktarımı                                                                                                                                    | Üstmetin transfer protokolü                                                                     |
| Mimari               | Yayınla/abone ol mimarisine sahiptir. Burada cihazlar herhangi bir konuyu yayınlayabilir ve ayrıca herhangi bir güncelleme için herhangi bir konuya abone olabilir. | İstek/yanıt anlamına gelen İstemci/Sunucu mimarisine sahiptir.                                  |
| Üst katman protokolü | TCP üzerinden çalışır.                                                                                                                                              | TCP ve UDP üzerinden çalışır.                                                                   |
| mesaj boyutu         | küçük, .                                                                                                                                                            | Büyük,                                                                                          |
| mesaj formatı        | 2Byte başlık ile ikili                                                                                                                                              | ASCII formatı.                                                                                  |
| Veri dağıtımı        | 1 ila 0/1/N                                                                                                                                                         | sadece bire bir, daha fazla POST                                                                |
| Veri güvenliği       | Evet, güvenlik için SSL/TLS kullanır                                                                                                                                | HAYIR, bu nedenle veri güvenliği sağlamak için HTTPS kullanılır                                 |
| karmaşıklık          | Basit                                                                                                                                                               | İstemci daha karmaşık (ASCII ayrıştırıcı)                                                       |
| şifreleme            | Yükü şifreler, yani yükten bağımsızdır                                                                                                                              | veriler iletimden önce şifrelenmez                                                              |
| Ne zaman kullanılır  | Projeniz, motor pompasını uyarlamak için buzdolabının termometre ile iletişim kurmasını sağlamaksa, MQTT’yi kolayca kullanabilirsiniz.                              | Dünyanın dört bir yanından büyük veri toplamanız gerekiyorsa, HTTP kullanmayı düşünebilirsiniz. |

## Çözüm:

MQTT Protokolü kullanımı kolaydır. Eğer projeniz, motor pompasını uyarlamak için buzdolabının termometre ile iletişim kurmasına izin vermekse, MQTT’yi kolayca kullanabilirsiniz, Büyük veri, yani dünyanın dört bir yanından büyük miktarda veri toplamanız gerekiyorsa, o zaman kullanmayı düşünmelisiniz. HTTP protokolü.

HTTP değerli ve genişletilebilir. Ancak MQTT, IoT geliştirme olarak adlandırıldığında daha uygundur.