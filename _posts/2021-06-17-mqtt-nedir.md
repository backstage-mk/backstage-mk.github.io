---
title: "MQTT Nedir?"
author: Mümin Köykıran
date: "2021-06-17"
categories: 
  - "Mqtt"
  - "IoT"
tags: 
  - "mqtt protokolü nedir"
  - "neden mqtt protokolü kullanılır"
image:
  src: /asset/mqtt-nedir/mqtt-2.jpg
---


## MQTT Nedir?
TCP/IP temelli olan ve IoT yani Nesnelerin İnterneti dünyasında vazgeçilmez olarak kullanılan bir haberleşme protokolüdür. Çalışma prensibi olarak Socket haberleşmelerinde olduğun gibi SUBSCRIBER ve BROKER mantığına dayanmaktadır. Günlük hayattan örnek vermek gerekirse bir web sitesinde abone ol formuna kendi e-posta bilgisi yazan bir kişi, o web sitesinden yayımlanan her bir yazı sonrasında nasıl haberdar ediliyor ise, bu protokolün çalışması sırasında da broker’a abone olan diğer client’lar veri yayımlayabilir ve diğer yayımlanan verileri görebilirler. Aslında bütünüyle geniş bir haberleşme ağı oluşturmaktadırlar.

MQTT protokolü başlıca akıllı ev sistemlerinde, akıllı şehirlerde vb. şeklinde başına akıllı getirilen ve ana bir merkez ile haberleşmesi gereken neredeyse her cihazda kullanımı uygundur. Enerji tüketim verilerini, sensorler vb. donanımlardan veri toplamaya ve göndermeye yönelik hızlı ve düşük maliyetli bir protokoldür.

![MQTT Artıları Nedir?](/asset/{{page.id | replace:'/posts/',''}}/mqtt-1.jpg)
*MQTT Artıları Nedir?*

## MQTT Artıları Nedir?
HTTP protokolünde gönderim sırasında kullanılan veri paketinin header kısmında olduğu gibi o paketin kimliğini ifade eden ‘gereksiz’ kısımlar yer almaz. Böylece düşük internet bantlarında daha hızlı çalışabilmektedir.
TCP/IP protokolü tabanlı olması sebebiyle verinin gidip karşı tarafa ulaşıp ulaşmadığının kontrolü de sağlanmaktadır.

İstenildiği takdirde haberleşmeye SSL sertifikası getirilerek şifreli bir haberleşme ağı kurulmuş olabilir. Bu alt yapının oluşmasındaki en büyük etken SSL/TLS desteğinin olmasıdır.

Haberleşme sırasında asenktron bir çalışma mevcuttur. Böylece çok fazla subscriber olması durumunda dahi sorunsuz çalışabilmektedir.
Açıklama: Bu koşulun yerine getirilmesi için broker olarak seçilen sunucular/serverler cihazın çoklu bağlantıları kaldırabilecek ve kolay kolay dar boğaz olmayan cihazlar olmalıdır.

Bu protokolün client tarafı düşük bantlı internet ağlarında daha dahi çalıştığı için düşük güç tüketimine sahiptir. Bu şekilde M2M yani Machine to Machine haberleşmeleri için biçilmiş kaftandır.

Sık aynı zamanda çoklu veri toplayan, bu verileri anlık olarak bir yerlerde gösterme ve veritabanlarına kaydetme işlemlerini yerine getiren tüm cihazlarda kullanılması mantıklı ve gereklidir.

Veri toplama yanında cihazlara komut gönderme ve cihazda yer alan sensor gibi komponenetlerden anlık geri bildirimleri kontrol merkezlerine göndermede etkilidir.