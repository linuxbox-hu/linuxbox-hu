---
excerpt: "Manapság az interneten robotok kutatnak a gyenge jelszavas felhasználók
  shelljei után. Meglehetősen kellemetlen dolog mikor látjuk a logjainkban a sikertelen
  belépési kísérleteket, mikor próbálgatják kitalálni a felhasználóink a jelszavát,
  usernevét.\r\n\r\nTermészetesen tudunk védekezni a probléma ellen.\r\nKét fejta
  egyszerű megoldás is van:\r\n\r\n1. Beállíthatunk egy speciálisan erre fejlesztett
  ssh démon konfigurációs paramétert: <strong>MaxStartups</strong>\r\n <strong>/etc/ssh/sshd_config</strong>
  konfigurációs állomány végén. További információt kahatunk a manuálokból. man sshd_config\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: SSH démon védelme
created: 1126296389
---
Manapság az interneten robotok kutatnak a gyenge jelszavas felhasználók shelljei után. Meglehetősen kellemetlen dolog mikor látjuk a logjainkban a sikertelen belépési kísérleteket, mikor próbálgatják kitalálni a felhasználóink a jelszavát, usernevét.

Természetesen tudunk védekezni a probléma ellen.
Két fejta egyszerű megoldás is van:

1. Beállíthatunk egy speciálisan erre fejlesztett ssh démon konfigurációs paramétert: <strong>MaxStartups</strong>
 <strong>/etc/ssh/sshd_config</strong> konfigurációs állomány végén. További információt kahatunk a manuálokból. man sshd_config

2. iptables tűzfal szabályokat is létrehozhatunk a problémára.
<strong>iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --set
iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j DROP</strong>
Például ez a két sor kizárja 1 percen belül a 4. próbálkozástól a következőket a 22 porton.

Sok már kevésbé egyszerű és szerintem veszélyesebb megoldás is van. Van aki kizár minden próbálkozást végleg a támadó tartományából... ezeket a megoldásokat én nem ismertetem. Feleslegesnek túlzásnak tartom őket.

De azért felsorolnék párat közülük:
<a href="http://gentoo-wiki.com/HOWTO_Protect_SSHD_with_Swatch">Swatch</a> egy ügyes tool   hasonló problémák kezelésére.
<a href="http://adam.rosi-kessel.org/weblog/free_software/code/ssh_login_blocker.html">Ssh login blokker</a> és egy újabb.
<a href="http://www.debian-administration.org/articles/187">További infó angolul.</a>
