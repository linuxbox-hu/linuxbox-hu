---
excerpt: "<a href=\"http://en.wikipedia.org/wiki/Dkim\">Domain Key Identified Mail
  (DKIM)</a> szolgáltatás hozzáad  a kimenő levelek fejlécéhez egy aláírást amivel
  azonosítja azokat, hogy valóban a mi domainünk levelező remdszere küldte a levelet.
  Miután a publikus kulcsot hozzáadtuk a DNS szerverünkbe mint TXT rekordot bárki
  tudja ellenőrizni, hogy a mi tartományunkból küldött levél valóban a mi szerverünkről
  érkezett-e vagy sem.\r\n\r\nA rendszer konfigurálását szeretném leírni a továbbiakban.\r\n"
categories:
- debian
layout: story
author: kecsi
title: DKIM és Postfix
created: 1245670759
---
<a href="http://en.wikipedia.org/wiki/Dkim">Domain Key Identified Mail (DKIM)</a> szolgáltatás hozzáad  a kimenő levelek fejlécéhez egy aláírást amivel azonosítja azokat, hogy valóban a mi domainünk levelező remdszere küldte a levelet. Miután a publikus kulcsot hozzáadtuk a DNS szerverünkbe mint TXT rekordot bárki tudja ellenőrizni, hogy a mi tartományunkból küldött levél valóban a mi szerverünkről érkezett-e vagy sem.

A rendszer konfigurálását szeretném leírni a továbbiakban.
<!--break-->
Mindenzt debian rendszeren meglévő postfix szerver módosításával teszem.
Először telepítsük fel a dkim-filter csomagot amit használni fogunk a domain key hozzádásához leveleinkhez.
<code>apt-get install dkim-filter</code>
(Debian Etch 4.0 alatt backports.org etch-backports repóból. Lenny alatt már nincs ilyen gond.)

Szerkesszük meg az alap konfigurációs állományt <code>/etc/dkim-filter.conf</code>
Ha több domaint kezel a rendszerünk akkor érdemes a <code>KeyList         /etc/dkim-keys.conf</code> sort kommentezését megszüntetni. Majd ezt az állományt létre is kell hozni. De előtte a /etc/dkim-filter/ könyvtárba kell generáljunk privát és publikus kulcsokat domainenként. (Megjegyzendő azonos is lehet a kulcs amivel aláírjuk a domaineket...)
A kulcsok létrehzásához használjuk a <code>dkim-genkey -b 1024 -d pelda.hu -s selector0</code> parancsot.

A létrehozott kulcsokat egyesével soronként adjuk be a már korábban emlegettt kulcs lista állományba(/etc/dkim-keys.conf). pl egy sor így nézzen ki:
<code>*@pelda.hu:pelda.hu:/etc/dkim-filter/selector0</code>
Lehet hogy modosítanunk kell a /etc/default/dkim-filter állományon is. Pl. így adhatjuk meg hogy milyen porton hallgasson a szolgáltatás.
<code>SOCKET="inet:8891@localhost"</code>

kész a konfigurálás {újra}elindithatjuk a dkim-filter szolgáltatást így:
<code>/etc/init.d/dkim-filter {re}start</code>

Ne felejtsük a DNS szerveünkbe létrehozni a TXT rekordot aminek az értékét a generált kulcs melletti pl. /etc/dkim-filter/selector0.txt állományból vehetjük.

Végül kezdjük el használni a levelező szerverünkkel a frissen bekonfigurált szolgáltatást. 
Adjuk pl a vegére az /etc/postix/main.cf állományba a következőt.
<code>
#DKIM
milter_default_action = accept
milter_protocol = 3
#smtpd_milters = unix:/var/run/dkim-filter/dkim-filter.sock
#non_smtpd_milters = unix:/var/run/dkim-filter/dkim-filter.sock
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891
</code>

Mire jó ez az egész? Hát ugye pl gmail, yahoo rendszerek fel fogják ismerni az aláírást és ellenőrzik azt így kevésbé minősítik leveleinket SPAMnek. Ilyen sort kell keressünk pl a gmail-re érkezett leveleinkben:
<code>Authentication-Results: pelda.hu; dkim=pass (1024-bit key) header.i=@gmail.com; dkim-asp=none</code>
