---
title: "Angular 8 – JWT Authentication Örneği"
author: Mümin Köykıran
date: "2021-07-28"
categories: 
  - "Angular"
  - "Ionic Framework"
  - "Web Güvenliği"
tags: 
  - "angular"
  - "angular 8"
  - "authentication"
  - "ionic"
  - "jwt"
  - "jwt authentication"
image:
  src: /asset/angular-8-jwt-authentication-ornegi/angular.jpg
---

Merhaba,

Ionic 4 Framework’ünün ve Angular 8’in kullanıldığı Target – Yeni Nesil ERP Yazılımımızda kullanıcı tarafında JWT Authentication alt yapısının nasıl getirildiğini sizlere kısaca bahsedeceğim. Gerekli kod çalışmasını ve denemesini ekte belirteceğim projeyi çalıştırarak sağlayabilirsiniz.

 ( [angular-8-jwt-authentication-example.zip](/asset/{{page.id | replace:'/posts/',''}}/angular-8-jwt-authentication-example.zip){:rel="nofollow"}{:target="_blank"} )

Ekte yer alan çalışmada JWT token verisinin backend üzerinden gelmesini simüle etmek amacıyla fake bir backend tasarlanmıştır. Route ettiği path üzerine gelen requeste, response olarak “fake-jwt-token” olarak dönmektedir. Bu veri normal şartlarda herhangi bir backend üzerinden HMAC SHA256 veya RSA algoritmaları kullanılarak şifrelebirler.

Bu örnek çalışmada token verimiz local storage üzerinde yer tutulmaktadır. Kullanıcı tarafından yapılan bir request işlemi sırasında post, get, put ,delete fark etmeksizin header kısmında

``` Typescript
Authorization: Bearer <token>
```
şeklinde token bilgimiz backend tarafına iletilmektedir.

Backend gelen token’i parse ederek içeriğini yine kendi içeriğinde yer alan veriler ile doğrulama sonrası backend tarafında yer alan key bilgisi ile de decryption işlemi sağlayarak, gerekli kontrolleri sağlamaktadır.

Ionic tarafında sağlıklı bir kullanım için sayfaların güvenlinin sağlanması gerekir bunun için app.routing.ts dosyasında her bir sayfa için guard kalıbının eklenmesi gerekmektedir. Örnek kullanım:

``` Typescript
const routes: Routes = [
    { path: '', component: HomeComponent, canActivate: [AuthGuard] },
    { path: 'login', component: LoginComponent },

    // otherwise redirect to home
    { path: '**', redirectTo: '' }
];
```

Bu özet çalışma bu kadardır. Daha detaylı bilgi için ekte yer alan çalışmayı indirip çalıştırabilir veya canlı demosunu aşağıdaki link üzerinden inceleyebilirsiniz.

## Reference
* https://stackblitz.com/edit/angular-8-jwt-authentication-example