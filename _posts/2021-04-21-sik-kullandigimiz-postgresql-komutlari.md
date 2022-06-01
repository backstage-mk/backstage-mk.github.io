---
title: "Sık Kullandığımız PostgreSQL Komutları"
date: "2021-04-21"
categories: 
  - "PostgreSQL"
  - "DevOps"
tags: 
  - "psql"
  - "PostgreSQL"
  - "veritabanı"
image:
  src: "/asset/sik-kullandigimiz-postgresql-komutlari/postgre-sql-dev-logo.jpg"
# pin: true
---


**Not** : Bu yazıda, PostgreSQL veritabanı sunucusundaki sık kullanılan komutları, verileri daha hızlı ve daha etkili bir şekilde sorgulamanıza yardımcı olan yaygın psql komutlarının bir listesini vermekteyim. [^ga-filters]

## 1) PostgreSQL veritabanına bağlanın

Aşağıdaki komut, belirli bir kullanıcı altındaki bir veritabanına bağlanır. `Enter` tuşuna bastıktan sonra PostgreSQL kullanıcının şifresini soracaktır.

```bash
psql -d database -U  user -W
```

Örneğin, `dvdrental` veritabanına `postgres` kullanıcısı ile bağlanmak için aşağıdaki komutu kullanılır:

```bash
C:\Program Files\PostgreSQL\9.5\bin>psql -d dvdrental -U postgres -W
Password for user postgres:
dvdrental=#
```

Başka bir host üzerinde bulunan bir veritabanına bağlanmak istiyorsanız, -h seçeneğini aşağıdaki gibi ekleyerek kullanıyorz:

```bash
psql -h host -d database -U user -W
```

Bağlantı için SSL modunu kullanmak istemeniz durumunda, aşağıdaki komutta gösterildiği gibi belirtmemiz yeterlidir:

```bash
psql -U user -h host "dbname=db sslmode=require"
```


## 2) Bağlantıyı yeni bir veri tabanına değiştirme

Bir veritabanına bağlandığınızda, bağlantıyı `user` tarafından belirlenen bir kullanıcı altında yeni bir veritabanına geçirebilirsiniz.

`user` parametresini atlarsanız, geçerli `user` varsayılır. Önceki bağlantı kapatılacak.


```bash
\c dbname username
```

Aşağıdaki komut, `postgres` kullanıcısı altındaki `dvdrental` veritabanına bağlanır:

```bash
postgres=# \c dvdrental
You are now connected to database "dvdrental" as user "postgres".
dvdrental=#
```


## 3) Mevcut veritabanlarını listeleme

Geçerli PostgreSQL veritabanı sunucusundaki tüm veritabanlarını listelemek için `\l` komutunu kullanın:


```bash
\l
```

## 4) Mevcut tabloları listeleme

Geçerli veritabanındaki tüm tabloları listelemek için `\dt` komutunu kullanın:

```bash
\dt
```

Bu komutun şu anda bağlı olan veritabanındaki tek tabloyu gösterdiğini unutmayın.

## 5) Bir tabloyu açıklayın

Sütun, tür, sütun değiştiriciler vb. Gibi bir tabloyu tanımlamak için aşağıdaki komutu kullanırsınız:


```bash
\d table_name
```

## 6) Mevcut şemayı listeleyin

Şu anda bağlı olan veritabanının tüm şemalarını listelemek için `\dn` komutu kullanırsınız.

```bash
\dn
```


## 7) Kullanılabilir işlevleri listeleyin

Mevcut veri tabanındaki mevcut fonksiyonları listelemek için `\df` komutu kullanırsınız.

```bash
\df
```


## 8) Mevcut görünümleri listeleyin

Mevcut veritabanındaki mevcut görünümleri listelemek için `\dv`komutu kullanırsınız.

```bash
\dv
```


## 9) Kullanıcıları ve rollerini listeleyin

Tüm kullanıcıları ve atama rollerini listelemek için şu `\du` komutu kullanırsınız:

```bash
\du
```

## 10) Önceki komutu yürütün

PostgreSQL sunucusunun mevcut sürümünü almak için `version()` aşağıdaki işlevi kullanırsınız :

```
SELECT version();
```


Şimdi, önceki komutu tekrar yazarak zaman kazanmak istiyorsanız, önceki komutu yürütmek için `\g` komutunu kullanabilirsiniz:

```bash
\g
```


psql, SELECT statement olan önceki komutu tekrar çalıştırır.

## 11) Komut geçmişi

Komut geçmişini görüntülemek için komutu kullanırsiniz `\s`.

```bash
\s
```


Komut geçmişini bir dosyaya kaydetmek istiyorsanız, dosya adını ve ardından `\s`  komutunu yazmanız gerekir :

```bash
\s filename
```


## 12) Bir dosyadan psql komutlarını yürütün

Bir dosyadan psql komutlarını çalıştırmak istemeniz durumunda `\i`, aşağıdaki şekilde bu komutu kullanabilirsiniz :

```bash
\i filename
```


## 13) psql komutları hakkında yardım alın

Mevcut tüm psql komutlarını bilmek için `\?` komutu kullanabilirsiniz.

```bash
\?
```


Belirli PostgreSQL deyimiyle ilgili yardım almak için şu `\h` komutu kullanabilirsniz .

Örneğin, ALTER TABLE deyimi hakkında ayrıntılı bilgi edinmek istiyorsanız, aşağıdaki komutu kullanırsınız:

```bash
\h ALTER TABLE
```


## 14) Sorgu yürütme süresini açın

Sorgu yürütme süresini açmak için `\timing` komutu kullanırsınız.

```bash
dvdrental=# \timing
Timing is on.
dvdrental=# select count(*) from film;
 count
-------
  1000
(1 row)
Time: 1.495 ms
dvdrental=#
```


Kapatmak için aynı komutu aşağıdaki gibi `\timing` şeklinde kullanırsınız.

```bash
dvdrental=# \timing
Timing is off.
dvdrental=#
```


## 15) Kendi düzenleyicinizde komutu düzenleyin

En sevdiğiniz düzenleyicide komutu yazabilmeniz çok kullanışlıdır. Bunu psql'de yapmak için `\e` komut verirsiniz. Komutu verdikten sonra psql, EDITOR ortam değişkeniniz tarafından tanımlanan metin düzenleyiciyi açar ve psql'de girdiğiniz en son komutu editöre yerleştirir.

![psql komutları](/asset/{{page.id | replace:'/posts/',''}}/psql-commands.jpg)

Komutu düzenleyiciye yazıp kaydedin ve düzenleyiciyi kapattıktan sonra, psql komutu çalıştıracak ve sonucu döndürecektir.

![psql komut örneği](/asset/{{page.id | replace:'/posts/',''}}/psql-command-example.jpg)

Düzenleyicide bir işlevi düzenlediğinizde daha kullanışlıdır.

```bash
\ef [function name]
```


![psql commadn ef düzenleme işlevi](/asset/{{page.id | replace:'/posts/',''}}/psql-command-ef-edit-function.jpg)

## 16) Çıkış seçeneklerini değiştirin

psql, bazı çıktı biçimi türlerini destekler ve çıktının anında nasıl biçimlendirileceğini özelleştirmenize olanak tanır.

-   `\a` komut hizalıdan hizalı olmayan sütun çıktısına geçer.
-   `\H` command çıktıyı HTML biçimine biçimlendirir.

## 17) psql'den çıkın

Psql'den çıkmak için `\q`command komutunu kullanın ve `enter`psql'den çıkmak için tuşuna basın .

```bash
\q
```

## Reference

[^ga-filters]: [https://www.postgresqltutorial.com/psql-commands/](https://www.postgresqltutorial.com/psql-commands/ "https://www.postgresqltutorial.com/psql-commands/"){:rel="nofollow"}{:target="_blank"}