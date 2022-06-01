---
title: "Sık Kullandığımız Docker Komutları"
date: "2021-04-22"
categories: 
  - "Docker"
  - "DevOps"
tags: 
  - "docker container"
image:
  src: "/asset/sik-kullandigimiz-docker-komutlari/docker.png"
# pin: true
---


Docker, uygulamayı bir konteyner içinde bağımlılıkları ile paketleyen ve çalıştıran bir konteynerizasyon sistemidir. Docker ile çalışırken sık kullandığımız ve bilinmesi gereken bazı docker komutu vardır. Bu makale tamamen bununlar ile ilgilidir.

## Kurulu olan docker sürümü bulmak

Bilmek isteyeceğiniz ilk şeylerden biri, kurulu docker sürümünü nasıl bulacağınızdır.

```console
mumin@ubuntu:/home/mumin$ docker --version
Docker version 18.09.6, build 481bc77
```


## Imaj indirme işlemi

[Docker](https://hub.docker.com/) görüntüsünü [dockerhub'dan](https://hub.docker.com/) (docker repository)  çekmeniz gerektiğini varsayalım. Aşağıdaki Apache HTTP sunucu görüntüsünü çekme örneğidir.

```console
mumin@ubuntu:/home/mumin$ docker pull httpd

Using default tag: latest
latest: Pulling from library/httpd
f5d23c7fed46: Pull complete
b083c5fd185b: Pull complete
bf5100a89e78: Pull complete
98f47fcaa52f: Pull complete
622a9dd8cfed: Pull complete
Digest: sha256:8bd76c050761610773b484e411612a31f299dbf7273763103edbda82acd73642
Status: Downloaded newer image for httpd:latest
mumin@ubuntu:/home/mumin$
```


## Imajları listeleme

TAG / IMAGE ID / SIZE şeklinde görüntü ayrıntılarıyla sistemde çekilen tüm docker görüntülerini listeleyin.

```console
mumin@ubuntu:/home/mumin$ docker images
REPOSITORY                 TAG                 IMAGE ID            CREATED             SIZE
httpd                      latest              ee39f68eb241        2 days ago          154MB
hello-world                latest              fce289e99eb9        6 months ago        1.84kB
sequenceiq/hadoop-docker   2.7.0               789fa0a3b911        4 years ago         1.76GB
```


## Çalıştırma işlemi

Komutta belirtilen docker imajını çalıştırın. Bu komut, Apache HTTP sunucusunun çalışacağı bir docker container yaratacaktır.

```console
mumin@ubuntu:/home/mumin$ docker run -it -d httpd
09ca6feb6efc0578951a3e2557ed5855b2edda39a795d9703eb54d975930fe6e
```



## O an çalışmakta olanları listeleme

`ps` tüm docker container'larının çalıştığı konteyner detaylarını listeler.

```console
mumin@ubuntu:/home/mumin$ docker ps

CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS               NAMES
09ca6feb6efc        httpd               "httpd-foreground"   36 seconds ago      Up 33 seconds       80/tcp              suspicious_bell
```


Gördüğünüz gibi, Apache sunucusu bu docker konteynerinda çalışıyor.

## ps -a komutu

Mevcuttaki containerları ayrıntılarıyla çalışan / durdurulan tüm docker container'larını listeleyin.

```console
mumin@ubuntu:/home/mumin$ docker ps -a

CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS                     PORTS                     	NAMES
09ca6feb6efc        httpd                            "httpd-foreground"       51 seconds ago      Up 49 seconds              80/tcp		            			suspicious_bell
2f6fb3381078        sequenceiq/hadoop-docker:2.7.0   "/etc/bootstrap.sh -d"   2 weeks ago         Exited (137) 9 days ago						                  	quizzical_raman
9f397feb3a46        sequenceiq/hadoop-docker:2.7.0   "/etc/bootstrap.sh -…"   2 weeks ago         Exited (255) 2 weeks ago   2122/tcp		            		determined_ritchie
9b6343d3b5a0        hello-world                      "/hello"                 2 weeks ago         Exited (0) 2 weeks ago					                   		peaceful_mclean
```



## exec komutu

Docker konteynerine erişin ve konteynerin içindeki komutları çalıştırın. Bu örnekte apache sunucu konteynerine erişiyoruz.

```console
mumin@ubuntu:/home/mumin$ docker exec -it 09ca6feb6efc bash
root@09ca6feb6efc:/usr/local/apache2# ls
bin  build  cgi-bin  conf  error  htdocs  icons  include  logs  modules

root@09ca6feb6efc:/usr/local/apache2#
```


Konteynerdan _çıkmak için exit yazın_ ve enter tuşuna basın.

## Konteyner kaldırma işlemi

Komutta belirtilen kapsayıcı kimliğine sahip docker konteynırını kaldırın.

```console
mumin@ubuntu:/home/mumin$ docker rm 9b6343d3b5a0
9b6343d3b5a0
```

Konteynırın kaldırılıp kaldırılmadığını kontrol etmek için aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ docker ps -a

CONTAINER ID        IMAGE                            COMMAND                  CREATED              STATUS                     PORTS                     NAMES
09ca6feb6efc        httpd                            "httpd-foreground"       About a minute ago   Up About a minute          80/tcp                    suspicious_bell
2f6fb3381078        sequenceiq/hadoop-docker:2.7.0   "/etc/bootstrap.sh -d"   2 weeks ago          Exited (137) 9 days ago                              quizzical_raman
9f397feb3a46        sequenceiq/hadoop-docker:2.7.0   "/etc/bootstrap.sh -…"   2 weeks ago          Exited (255) 2 weeks ago   2122/tcp                  determined_ritchie
```

## Imajın kaldırılması

Komutta belirtilen docker görüntü kimliğiyle docker görüntüsünü kaldırın

```console
mumin@ubuntu:/home/mumin$ docker rmi fce289e99eb9

Untagged: hello-world:latest
Untagged: hello-world@sha256:41a65640635299bab090f783209c1e3a3f11934cf7756b09cb2f1e02147c6ed8
Deleted: sha256:fce289e99eb9bca977dae136fbe2a82b6b7d4c372474c9235adc1741675f587e
Deleted: sha256:af0b15c8625bb1938f1d7b17081031f649fd14e6b233688eea3c5483994a66a3

mumin@ubuntu:/home/mumin$
```


## Docker'ı yeniden başlatma

Docker konteynerini komutta belirtilen konteyner kimliğiyle yeniden başlatın.

```console
mumin@ubuntu:/home/mumin$ docker restart 09ca6feb6efc

09ca6feb6efc
```

Aşağıdaki komutu çalıştırın ve konteynırın yakın zamanda başlatılıp başlatılmadığını doğrulamak için STATUS parametresini kontrol edin.

```console
mumin@ubuntu:/home/mumin$ docker ps

CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS               NAMES
09ca6feb6efc        httpd               "httpd-foreground"   6 minutes ago       Up 9 seconds        80/tcp              suspicious_bell
```


## Çalışmakta olan Docker'ı durdurma

Komutta belirtilen konteynır kimliğine sahip bir konteynırı durdurun.

```console
mumin@ubuntu:/home/mumin$ docker stop 09ca6feb6efc

09ca6feb6efc
```

Konteynırın hala çalışıp çalışmadığını veya durup durmadığını kontrol etmek için aşağıdaki komutu kullanırız.

```console
mumin@ubuntu:/home/mumin$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

## Docker'ı başlatma

Docker'daki bu komut, komutta belirtilen konteyner kimliğiyle docker konteynerini başlatır.

```console
mumin@ubuntu:/home/mumin$ docker start 09ca6feb6efc
09ca6feb6efc
```


Konteynerin başlayıp başlamadığını kontrol etmek için aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ docker ps
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS               NAMES
09ca6feb6efc        httpd               "httpd-foreground"   8 minutes ago       Up 3 seconds        80/tcp              suspicious_bell
```

## kill komutu kullanımı

Docker konteynerini kullanıldığında hemen durdurur. Docker stop komutu, konteynırı zarif bir şekilde durdurur; kill ve stop komutları arasındaki fark budur.

```console
mumin@ubuntu:/home/mumin$ docker kill 09ca6feb6efc

09ca6feb6efc
```

Konteynerin durdurulup durdurulmadığını görmek için aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```


## commit komutu kullanımı

Yerel sistemdeki komutta belirtilen konteynır kimliğiyle yeni bir docker imajı kaydedin. Aşağıdaki örnekte, mumin kullanıcı adıdır ve httpd_image görüntü adıdır.

```console
mumin@ubuntu:/home/mumin$ docker commit 09ca6feb6efc mumin/httpd_image
sha256:d1933506f4c1686ab1a1ec601b1a03a17b41decbc21d8acd893db090a09bb31c
```



## login komutu kullanımı

Docker hub'a giriş yapın. Docker hub kimlik bilgilerinizden oturum açmanız istenecektir.

```console
mumin@ubuntu:/home/mumin$ docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: mumin
Password:
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store
Login Succeeded
```



## push komutu kullanımı

Dockerhub'daki komutta belirtilen görüntü adına sahip bir docker görüntüsü yükleyin.

```console
mumin@ubuntu:/home/mumin$ docker push mumin/httpd_image
The push refers to repository [docker.io/mumin/httpd_image]
734d9104a6a2: Pushed
635721fc6973: Mounted from library/httpd
bea448567d6c: Mounted from library/httpd
bfaa5f9c3b51: Mounted from library/httpd
9d542ac296cc: Mounted from library/httpd
d8a33133e477: Mounted from library/httpd
latest: digest: sha256:3904662761df9d76ef04ddfa5cfab764b85e3eedaf10071cfbe2bf77254679ac size: 1574
```



## docker network komutu kullanımı

Docker'daki aşağıdaki komut, docker'a ait tüm ağın ayrıntılarını listeler.

```console
mumin@ubuntu:/home/mumin$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
85083e766f04        bridge              bridge              local
f51d1f3379e0        host                host                local
5e5d9a192c00        none                null                local
```


Başka docker ağ komutu vardır.

```console
mumin@ubuntu:/home/mumin$ docker network
Usage:  docker network COMMAND
Manage networks
Commands:
connect     Connect a container to a network
create      Create a network
disconnect  Disconnect a container from a network
inspect     Display detailed information on one or more networks
ls          List networks
prune       Remove all unused networks
rm          Remove one or more networks
Run 'docker network COMMAND --help' for more information on a command.
```


## Docker bilgisi

Çekirdek sürümü, kapsayıcı sayısı ve imajlar dahil olmak üzere sistemde yüklü olan docker hakkında ayrıntılı bilgi alın.

```console
mumin@ubuntu:/home/mumin$ docker info
Containers: 3
Running: 1
Paused: 0
Stopped: 2
Images: 3
Server Version: 18.09.6
Storage Driver: overlay2
Backing Filesystem: extfs
Supports d_type: true
Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
Volume: local
Network: bridge host macvlan null overlay
Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: bb71b10fd8f58240ca47fbb579b9d1028eea7c84
runc version: 2b18fe1d885ee5083ef9f0838fee39b62d653e30
init version: fec3683
Security Options:
apparmor
seccomp
Profile: default
Kernel Version: 4.18.0-25-generic
Operating System: Ubuntu 18.10
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 4.982GiB
Name: mumin
ID: RBCP:YGAP:QG6H:B6XH:JCT2:DTI5:AYJA:M44Z:ETRP:6TO6:OPAY:KLNJ
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Username: mumin
Registry: https://index.docker.io/v1/
Labels:
Experimental: false
Insecure Registries:
127.0.0.0/8
Live Restore Enabled: false
Product License: Community Engine
```


## Dosya kopyalama işlemi

Docker container'daki bir dosyayı yerel sisteme kopyalama sırasında gereken işlemler.

Bu örnekte, 09ca6feb6efc kimliğine sahip bir docker kapsayıcısının içindeki httpd.pid dosyasını /home/mumin/ konumuna kopyalıyoruz.

```console
mumin@ubuntu:/home/mumin$ sudo docker cp 09ca6feb6efc:/usr/local/apache2/logs/httpd.pid /home/mumin/
[sudo] password for mumin:
```


Dosyanın kopyalanıp kopyalanmadığını kontrol etmek için aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ ls
Desktop  Documents  example  examples.desktop  httpd.pid  nginx_new.yml  nginx.yml
```

## Geçmişi kontrol etme

Komutta belirtilen imaj adıyla bir docker imajının geçmişini gösterir.

```console
mumin@ubuntu:/home/mumin$ docker history httpd

IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
ee39f68eb241        2 days ago          /bin/sh -c #(nop)  CMD ["httpd-foreground"]     0B
<missing>           2 days ago          /bin/sh -c #(nop)  EXPOSE 80                    0B
<missing>           2 days ago          /bin/sh -c #(nop) COPY file:c432ff61c4993ecd…   138B
<missing>           4 days ago          /bin/sh -c set -eux;   savedAptMark="$(apt-m…   49.1MB
<missing>           4 days ago          /bin/sh -c #(nop)  ENV HTTPD_PATCHES=           0B
<missing>           4 days ago          /bin/sh -c #(nop)  ENV HTTPD_SHA256=b4ca9d05…   0B
<missing>           4 days ago          /bin/sh -c #(nop)  ENV HTTPD_VERSION=2.4.39     0B
<missing>           4 days ago          /bin/sh -c set -eux;  apt-get update;  apt-g…   35.4MB
<missing>           4 days ago          /bin/sh -c #(nop) WORKDIR /usr/local/apache2    0B
<missing>           4 days ago          /bin/sh -c mkdir -p "$HTTPD_PREFIX"  && chow…   0B
<missing>           4 days ago          /bin/sh -c #(nop)  ENV PATH=/usr/local/apach…   0B
<missing>           4 days ago          /bin/sh -c #(nop)  ENV HTTPD_PREFIX=/usr/loc…   0B
<missing>           5 days ago          /bin/sh -c #(nop)  CMD ["bash"]                 0B
<missing>           5 days ago          /bin/sh -c #(nop) ADD file:71ac26257198ecf6a…   69.2MB
```

## Logları kontrol etme

Komutta belirtilen içerilen id ile docker konteynerinin loglarını gösterin.

```console
mumin@ubuntu:/home/mumin$ docker logs 09ca6feb6efc
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Jul 15 14:01:55.400472 2019] [mpm_event:notice] [pid 1:tid 140299791516800] AH00489: Apache/2.4.39 (Unix) configured -- resuming normal operations
[Mon Jul 15 14:01:55.400615 2019] [core:notice] [pid 1:tid 140299791516800] AH00094: Command line: 'httpd -D FOREGROUND'
[Mon Jul 15 14:08:36.798229 2019] [mpm_event:notice] [pid 1:tid 140299791516800] AH00491: caught SIGTERM, shutting down
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Jul 15 14:08:38.259870 2019] [mpm_event:notice] [pid 1:tid 139974087980160] AH00489: Apache/2.4.39 (Unix) configured -- resuming normal operations
[Mon Jul 15 14:08:38.260007 2019] [core:notice] [pid 1:tid 139974087980160] AH00094: Command line: 'httpd -D FOREGROUND'
[Mon Jul 15 14:09:01.540647 2019] [mpm_event:notice] [pid 1:tid 139974087980160] AH00491: caught SIGTERM, shutting down
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Jul 15 14:10:43.782606 2019] [mpm_event:notice] [pid 1:tid 140281554879616] AH00489: Apache/2.4.39 (Unix) configured -- resuming normal operations
[Mon Jul 15 14:10:43.782737 2019] [core:notice] [pid 1:tid 140281554879616] AH00094: Command line: 'httpd -D FOREGROUND'
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Jul 15 14:14:08.270906 2019] [mpm_event:notice] [pid 1:tid 140595254346880] AH00489: Apache/2.4.39 (Unix) configured -- resuming normal operations
[Mon Jul 15 14:14:08.272628 2019] [core:notice] [pid 1:tid 140595254346880] AH00094: Command line: 'httpd -D FOREGROUND'
```

## İmaj arama komutu

Komutta belirtilen adla dockerhub'da bir docker imajını arama işlemi.

```console
mumin@ubuntu:/home/mumin$ docker search hadoop

NAME                             DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
sequenceiq/hadoop-docker         An easy way to try Hadoop                       611                                     [OK]
uhopper/hadoop                   Base Hadoop image with dynamic configuration…   98                                      [OK]
harisekhon/hadoop                Apache Hadoop (HDFS + Yarn, tags 2.2 - 2.8)     54                                      [OK]
bde2020/hadoop-namenode          Hadoop namenode of a hadoop cluster             22                                      [OK]
kiwenlau/hadoop                  Run Hadoop Cluster in Docker Containers         19
izone/hadoop                     Hadoop 2.8.5 Ecosystem fully distributed, Ju…   14                                      [OK]
uhopper/hadoop-namenode          Hadoop namenode                                 9                                       [OK]
bde2020/hadoop-datanode          Hadoop datanode of a hadoop cluster             9                                       [OK]
singularities/hadoop             Apache Hadoop                                   8                                       [OK]
uhopper/hadoop-datanode          Hadoop datanode                                 7                                       [OK]
harisekhon/hadoop-dev            Apache Hadoop (HDFS + Yarn) + Dev Tools + Gi…   6                                       [OK]
```

## Konfigürasyonları güncelleme

Konteynır yapılandırmalarını güncelleyin. Bu işlem tüm güncelleme seçeneklerini gösterir.

```console
mumin@ubuntu:/home/mumin$ docker update --help
Usage:  docker update [OPTIONS] CONTAINER [CONTAINER...]
Update configuration of one or more containers
Options:
--blkio-weight uint16        Block IO (relative weight), between 10 and 1000, or 0 to disable
(default 0)
--cpu-period int             Limit CPU CFS (Completely Fair Scheduler) period
--cpu-quota int              Limit CPU CFS (Completely Fair Scheduler) quota
--cpu-rt-period int          Limit the CPU real-time period in microseconds
--cpu-rt-runtime int         Limit the CPU real-time runtime in microseconds
-c, --cpu-shares int             CPU shares (relative weight)
--cpus decimal               Number of CPUs
--cpuset-cpus string         CPUs in which to allow execution (0-3, 0,1)
--cpuset-mems string         MEMs in which to allow execution (0-3, 0,1)
--kernel-memory bytes        Kernel memory limit
-m, --memory bytes               Memory limit
--memory-reservation bytes   Memory soft limit
--memory-swap bytes          Swap limit equal to memory plus swap: '-1' to enable unlimited swap
--restart string             Restart policy to apply when a container exits
```


Docker konteynırının CPU yapılandırmasını komutta belirtilen konteynır kimliği ile güncellemek için aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ docker update -c 1 2f6fb3381078

2f6fb3381078
```

## docker volume komutu kullanımı

Docker konteynerinin verileri depolamak için kullanacağı bir birim oluşturun.

```console
mumin@ubuntu:/home/mumin$ docker volume create
7e7bc886f69bb24dbdbf19402e31102a25db91bb29c56cca3ea8b0c611fd9ad0
```


Birim oluşturulmuşsa veya oluşturulmamışsa aşağıdaki komutu çalıştırın.

```console
mumin@ubuntu:/home/mumin$ docker volume ls
DRIVER              VOLUME NAME
local               7e7bc886f69bb24dbdbf19402e31102a25db91bb29c56cca3ea8b0c611fd9ad0
```


## Eklenti yükleme işlemi

Hata ayıklama ortamı 1 olarak ayarlanmış bir docker eklentisi vieux / sshfs kurun.

```console
mumin@ubuntu:/home/mumin$ docker plugin install vieux/sshfs DEBUG=1
Plugin "vieux/sshfs" is requesting the following privileges:
- network: [host]
- mount: [/var/lib/docker/plugins/]
- mount: []
- device: [/dev/fuse]
- capabilities: [CAP_SYS_ADMIN]
Do you grant the above permissions? [y/N] y
latest: Pulling from vieux/sshfs
52d435ada6a4: Download complete
Digest: sha256:1d3c3e42c12138da5ef7873b97f7f32cf99fb6edde75fa4f0bcf9ed277855811
Status: Downloaded newer image for vieux/sshfs:latest
Installed plugin vieux/sshfs
Run the below command to list the docker plugins.
mumin@ubuntu:/home/mumin$ docker plugin ls

ID                  NAME                 DESCRIPTION               ENABLED
2a32d1fb95af        vieux/sshfs:latest   sshFS plugin for Docker   true
```

## docker logout komutu kullanımı

Dockerhub'dan çıkış yapılıyor.

```console
mumin@ubuntu:/home/mumin$ docker logout
Removing login credentials for https://index.docker.io/v1/
```

**Sonuç** [^ga-filters]

Umarım şimdiye kadar ki docker komutları işinize yarar :)

## Reference

[^ga-filters]: [https://geekflare.com/docker-commands/](https://geekflare.com/docker-commands/ "https://geekflare.com/docker-commands/"){:rel="nofollow"}{:target="_blank"}