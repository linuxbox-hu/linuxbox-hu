---
excerpt: "Mostanában egyre több oldal ajánlja fel belépési mechanizmusként az [http://openid.net/
  OpenID]-t, amivel is egy elosztott azonosítási rendszerhez jutunk.\r\n\r\nCsakhogy
  szükség van arra, hogy valaki azonosítson. Én nagyon nem szeretném, ha engem olyan
  szerveren tartanának nyilván amit nem én felügyelek, főleg akkor ha az ott tárolt
  adataimmal sok weboldalhoz, alkalmazáshoz hozzáférhetnek - esetleg a tudtom nélkül.\r\n"
categories:
- linux
layout: story
author: szimszon
title: OpenID házilag egy PHP scripttel
created: 1211293561
---
Mostanában egyre több oldal ajánlja fel belépési mechanizmusként az [http://openid.net/ OpenID]-t, amivel is egy elosztott azonosítási rendszerhez jutunk.

Csakhogy szükség van arra, hogy valaki azonosítson. Én nagyon nem szeretném, ha engem olyan szerveren tartanának nyilván amit nem én felügyelek, főleg akkor ha az ott tárolt adataimmal sok weboldalhoz, alkalmazáshoz hozzáférhetnek - esetleg a tudtom nélkül.
<!--break-->
Kicsit keresgéltem, és akkor találtam egy egyszerű php scriptre, amivel saját magamnak készíthetek OpenID szolgáltatást és csak egy php képes webszerver kell hozzá.

A scriptről leírás [http://siege.org/projects/phpMyID/ itt].
Ahol találtam [http://intertwingly.net/blog/2007/01/03/OpenID-for-non-SuperUsers itt].
