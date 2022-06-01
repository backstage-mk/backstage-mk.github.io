---
title: "Orange Pi için Node-RED Kurulumu"
date: "2020-12-13"
categories: 
  - "node-red"
  - "orange-pi"
tags: 
  - "linux-node-red-kurulumu"
  - "linux-nodejs-kurulumu"
  - "nodejs-kurulumu"
  - "nodered-kurulumu"
  - "orange-pi-node-red-kurulumu"
  - "orangen-pi-nodejs-kurulumu"
image:
  src: "/asset/orange-pi-icin-node-red-kurulumu/image-1.png"
# pin: true
---

Merhaba, elimdeki **Orange Pi Lite** cihazına **Node-RED** kurulumu sırasında izlediğim aşamaları kendim için daha sonrada kullanabilmek ve siz değerli okurlara da katkı sağlayacağını düşündüğüm için bu paylaşımı yapıyorum, hazırlanan adımları takip ederek sizde kolay ve hızlı bir şekilde kurulumu gerçekleştirebilirsiniz.

Node-RED'in çalışması için ilk kurulması gereken NodeJs'dir.

## Adım 1: NodeJs Kurulumu

Yazının hazırlandığı zaman diliminde Node-RED'in kendi sitesinde belirttiği üzere önerdiği versiyon _12.x_ olarak belirtilmiştir.

> Node-RED currently recommends **Node 12.x LTS**.

| Version | Support Level | Notes |
| --- | --- | --- |
| < 8.x | _Unsupported_ |   |
| **8.x** | _Supported_ | No longer maintained |
| **10.x** | _Supported_ | Reaches end-of-life April 2021 |
| **12.x** | **Recommended** |   |
| **14.x** | Supported |   |

Kaynak: [\[1\]](https://nodered.org/docs/faq/node-versions)

NodeJs Kurulumu için:

```console
curl -sL https://deb.nodesource.com/setup\_7.x | sudo -E bash -
sudo apt-get install -y nodejs
```


## Adım 2: Node-RED Kurulumu

```console
sudo npm install -g --unsafe-perm node-red
```

## Adım 3: Node-RED'i Başlatma

```console
root@ArtexAI:~# node-red
13 Dec 18:30:21 - [info]
 
Welcome to Node-RED
===================
 
13 Dec 18:30:21 - [info] Node-RED version: v1.2.6
13 Dec 18:30:21 - [info] Node.js  version: v12.20.0
13 Dec 18:30:21 - [info] Linux 3.4.113-sun8i arm LE
13 Dec 18:30:23 - [info] Loading palette nodes
13 Dec 18:30:26 - [info] Settings file  : /root/.node-red/settings.js
13 Dec 18:30:26 - [info] Context store  : 'default' [module=memory]
13 Dec 18:30:26 - [info] User directory : /root/.node-red
13 Dec 18:30:26 - [warn] Projects disabled : editorTheme.projects.enabled=false
13 Dec 18:30:26 - [info] Flows file     : /root/.node-red/flows_ArtexAI.json
13 Dec 18:30:26 - [info] Creating new flow file
13 Dec 18:30:26 - [warn]
 
---------------------------------------------------------------------
Your flow credentials file is encrypted using a system-generated key.
 
If the system-generated key is lost for any reason, your credentials
file will not be recoverable, you will have to delete it and re-enter
your credentials.
 
You should set your own key using the 'credentialSecret' option in
your settings file. Node-RED will then re-encrypt your credentials
file using your chosen key the next time you deploy a change.
---------------------------------------------------------------------
 
13 Dec 18:30:26 - [info] Starting flows
13 Dec 18:30:26 - [info] Started flows
13 Dec 18:30:26 - [error] Unable to listen on http://127.0.0.1:1880/
13 Dec 18:30:26 - [error] Error: port in use
```

## Adım 4: Yeni Modül Ekleme

```console
cd $HOME/.node-red
npm install <npm-package-name>
```

[Node-RED kitaplığında](https://flows.nodered.org/) neredeyse tüm ihtiyaçlarını karşılayacak modüller yer almaktadır. Yazı içerisinde örnek olması açısından _Orange Pi GPIO_ modülü kurulacaktır.

```console
sudo npm install node-red-contrib-opi-gpio
```

Node-RED'i yeniden başlatın ve web tarayıcınız üzerinden http://orange\_pi\_ip:1880/ şeklinde Node-RED'e erişim sağlayabilirsiniz.

![](/asset/orange-pi-icin-node-red-kurulumu/image.png)
**Node-RED dashboard'una ait ekran görüntüsü**

## Adım 5: Node-RED'in Orange Pi Boot Sonrası Otomatik Yeniden Açılmasını Sağlama

Bunun için gerekli olan servis dosyalarını indiriyoruz. (nodered.service servis dosyası ve start, stop dosyaları)

```console
sudo wget https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/nodered.service -O /lib/systemd/system/nodered.service
sudo wget https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/node-red-start -O /usr/bin/node-red-start
sudo wget https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/node-red-stop -O /usr/bin/node-red-stop
sudo chmod +x /usr/bin/node-red-st*
sudo systemctl daemon-reload
```

Aşağıdaki komut ile servis dosyasında bazı düzenlemeler yapılması gerekmektedir.

```console
sudo nano /lib/systemd/system/nodered.service
```

`nodered.service` dosyası içeriğini aşağıdaki şekilde değiştirmemiz gerekmektedir. Bunun sebebi az önce indirilen servis dosyaları _raspberry pi_ için hazırlanmıştır. Biz ise _orange pi_ için gerekli ayarlamaları sağlayacağız.

```console
# systemd service file to start Node-RED
[Unit]
Description=Node-RED graphical event wiring tool.
Wants=network.target
Documentation=http://nodered.org/docs/hardware/raspberrypi.html
[Service]
Type=simple
# Run as root user in order to have access to gpio pins
User=root
Group=root
Nice=5
Environment="NODE_OPTIONS=--max-old-space-size=128"
#Environment="NODE_RED_OPTIONS=-v"
ExecStart=/usr/bin/env node-red-pi $NODE_OPTIONS $NODE_RED_OPTIONS
KillSignal=SIGINT
Restart=on-failure
SyslogIdentifier=Node-RED
[Install]
WantedBy=multi-user.target
```

Sistem her boot olduğunda Node-RED servisinin yeniden başlaması için gerekli olan etkinleştirmeleri sağlıyoruz.

```console
sudo systemctl daemon-reload
sudo systemctl enable nodered.service
```

sudo systemctl daemon-reload
sudo systemctl enable nodered.service

Eğer ki başlangıçta otomatik Node-RED servisinin aktif olmasını istemezseniz aşağıdaki komut ile de servisi tekrardan devre dışı bırakabilirsiniz.

```console
sudo systemctl disable nodered.service
```