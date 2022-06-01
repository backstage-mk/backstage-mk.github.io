---
title: "PhpMyAdmini Manuel Olarak Yükseltme"
date: "2021-04-21"
categories: 
  - "linux"
  - "phpmyadmin"
tags: 
  - "upgrade"
  - "mysql"
  - "php"
  - "phpmyadmin"
image:
  src: "/asset/phpmyadmini-manuel-olarak-yukseltme/phpmyadmin-logo.png"
# pin: true
---

Sunucunuzda yer alan phpMyAdmin'in en son sürümüne geçiş yapma istiyor veya mevcut sürümünüzle uyumluluk sorunları yaşıyorsanız, bu makale ile birlikte phpMyAdmin'in en son sürümünü manuel olarak indirip kurabileceğiniz adımları anlatacağım. [^ga-filters]

## Giriş

Bu kılavuz Ubuntu 20.10 ve Ubuntu 16.04 sürümlerinde test edilmiştir. Ayrıca diğer Debian tabanlı dağıtımlar için de sorunsuz çalışmalıdır. Bu arada, bu kılavuzu nasıl geliştireceğiniz konusunda herhangi bir öneriniz varsa, lütfen yorumlarda bana bildirin.

## 1. phpMyAdmin'i yedekleme

Herhangibir aksiliğe karşı, işlemlere başlamadan önce mevcut phpMyAdmin klasörünüzü yeniden adlandırarak yedekleyelim.

```console
sudo mv /usr/share/phpmyadmin/ /usr/share/phpmyadmin.bak
```

Yeni bir phpMyAdmin klasörü oluşturalım

```console
sudo mkdir /usr/share/phpmyadmin/
```

Oluşturduğumuz dizine geçelim

```console
cd /usr/share/phpmyadmin/
```

## 2. phpMyAdmin'i İndirin ve Çıkarın

**Şubat 2020 Güncellemesi:** phpMyAdmin 5 yayınlandı ancak yalnızca **PHP 7.1** ve üstü ile uyumludur. PHP sürümünüzü komut satırında bulmak için `php -v` komutunu çalıştırın.

phpMyAdmin sürüm 4.x artık yalnızca güvenlik düzeltmelerinin ve kritik hata düzeltmelerinin yapıldığı LTS aşamasındadır. Kullanıcıların sürüm 5'e geçmeleri önerilir ( [daha fazlasını okuyun](https://www.phpmyadmin.net/news/2020/1/8/phpmyadmin-494-and-501-are-released/){:rel="nofollow"}{:target="_blank"} ).


- [ ]  **PHP 7.1** ve üstü için **phpMyAdmin 5.x**'i indirin
- [ ]  **PHP 5.5** - **PHP 7.4** için **phpMyAdmin-4.9.7**'yi indirin

[**PhpMyAdmin indirme sayfasını**](https://www.phpmyadmin.net/downloads/){:rel="nofollow"}{:target="_blank"} ziyaret edin ve .tar.gz URL'sini bulun ve `wget` komutunu kullanarak indirin. 

Bu kılavuzda Şubat 2021'de yayınlanan 5.1.0 sürümünü kullanıyoruz. Daha sonraki bir sürüm artık mevcutsa, aşağıdaki komutları eşleşecek şekilde değiştirdiğinizden emin olun (ve kılavuzu güncelleyebilmem için yorumlarda bana bildirin). PhpMyAdmin 5.x ile sorun yaşıyorsanız, bunun yerine phpMyAdmin-4.9.7'yi deneyin.

```bash
sudo wget https://files.phpmyadmin.net/phpMyAdmin/5.1.0/phpMyAdmin-5.1.0-all-languages.tar.gz
```

İndirdiğiniz tar.gz dosyasını çıkarın

```bash
sudo tar xzf phpMyAdmin-5.1.0-all-languages.tar.gz
```

Çıkartıldıktan sonra klasör içeriğini listeleyin

```bash
ls
```

Yeni bir `phpMyAdmin-5.1.0-all-languages` klasörü görmelisiniz 

Bu klasörün içeriğini şuraya taşımak istiyoruz: `/usr/share/phpmyadmin`

```bash
sudo mv phpMyAdmin-5.1.0-all-languages/* /usr/share/phpmyadmin
```

Artık phpMyAdmin'de tekrar oturum açabilir ve mevcut sürümü kontrol edebilirsiniz. Bu arada aşağıdaki görselde yer aldığı gibi iki adet hata görebilirsiniz:

![phpMyadmin blowfish gizli hatası ve tempdir yazılabilir değil hatası](/asset/{{page.id | replace:'/posts/',''}}/phpmyadmin-blowfish-tempdir-not-accessible.png)

## 3. vendor_config.php dosyasını düzenleyin

Şeklinde bir hata görüyorsanız `$cfg['TempDir'] (./tmp/)` erişilebilir değil. phpMyAdmin şablonları önbelleğe alamaz ve bu nedenle yavaşlayacaktır.

`vendor_config.php` dosyasını açın

```bash
sudo nano /usr/share/phpmyadmin/libraries/vendor_config.php
```

`CTRL`+`W` ya basın ve `TEMP_DIR` aratın

Şununla değiştirin:

```

/usr/share/phpmyadmin/libraries/vendor_config.php


define('TEMP_DIR', '/var/lib/phpmyadmin/tmp/');
```

Ayrıca bir hata görebilirsiniz _. Konfigürasyon dosyası artık gizli bir parola gerektiriyor (blowfish_secret)._ Blowfish sırrı phpMyAdmin tarafından tanımlama bilgisi kimlik doğrulaması için kullanılır. 
`CTRL` + `W` 'ya basın ve `CONFIG_DIR` aratın 

Şununla değiştir:

```

/usr/share/phpmyadmin/libraries/vendor_config.php


define('CONFIG_DIR', '/etc/phpmyadmin/');
```

phpMyAdmin artık kurulum dizinine bağlı olarak kendi blowfish sırrını oluşturacaktır.

Dosyayı kaydedin ve çıkın. ( `CTRL` + `X` tuşuna basın sonra `Y` basın ve ardından `ENTER` tuşuna basın)

Şimdi phpMyAdmin'de tekrar oturum açın ve hataların giderildiğinden emin olun.

“The secret passphrase in configuration (blowfish_secret) is too short.” şeklinde bir hata görüyorsanız, aşağıya bakınız.

PhpMyAdmin 5 ile sorun yaşıyorsanız, bunun yerine phpMyAdmin-4.9.7'yi deneyin, çünkü bu PHP 7.0 ve altı ve MySQL 5.4 ve altı için en son kararlı sürümdür.

## 4. Temizleme

Her şey sorunsuz tamamlandığına göre tar.gz dosyasını ve boş klasörü silebilirsiniz.

```bash
sudo rm /usr/share/phpmyadmin/phpMyAdmin-5.1.0-all-languages.tar.gz
```

```bash
sudo rm -rf /usr/share/phpmyadmin/phpMyAdmin-5.1.0-all-languages
```

Yeni phpMyAdmin kurulumunuzun doğru çalıştığından eminseniz, yedekleme klasörünü silebilirsiniz.

```bash
sudo rm -rf /usr/share/phpmyadmin.bak
```

Yaşasın!

## "(blowfish_secret) is too short" Hatası 

“The secret passphrase in configuration (blowfish_secret) is too short.” şeklinde bir hata görüyorsanız;

`blowfish_secret.inc.php` dosyasını açın:

```bash
sudo nano /var/lib/phpmyadmin/blowfish_secret.inc.php
```

[32 karakterli rastgele bir ifade oluşturmak için buraya tıklayın.](https://passgen.co/?pw=32&a=1){:rel="nofollow"}{:target="_blank"}

Kopyalayın ve blowfish_secret.inc.php'ye yapıştırın.

```php

/var/lib/phpmyadmin/blowfish_secret.inc.php


<?php
$cfg['blowfish_secret'] = '32_char_random_phrase_here';
```

Kaydedin ve çıkın ( `CTRL`+ `X` tuşlarına basın sonra `Y` tuşuna ve ardından `ENTER` tuşuna basın)

Yapılması gereken işlemler bu kadar. Bir sonraki yazıda görüşmek dileğiyle :)

## Reference

[^ga-filters]: [https://devanswers.co/manually-upgrade-phpmyadmin/](https://devanswers.co/manually-upgrade-phpmyadmin/ "https://devanswers.co/manually-upgrade-phpmyadmin/"){:rel="nofollow"}{:target="_blank"}