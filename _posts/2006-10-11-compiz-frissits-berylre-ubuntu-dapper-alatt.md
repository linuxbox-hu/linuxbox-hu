---
excerpt: "Tegnap kíváncsiságból feltelepítettem a <a href=\"http://www.beryl-project.org/\">Beryl-t</a>
  lecserélve az eddigi <a href=\"/xgl_compiz\">compiz</a> ablakmenedzserem.\r\n\r\nItt
  találtam segítséget: <a href=\"http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL\">1</a>,
  <a href=\"http://ubuntuforums.org/showthread.php?t=268036\">2</a>\r\n\r\nA dolog
  meglehetősen egyszerű volt:\r\nEgyenlőre az X szerverem békén hagytam (XGL-t), csak
  a beryl csomagokat telepítettem fel.\r\nElőször hozzáadtam a megfelelő csomag repot
  apt-hoz:\r\n<code>\r\n# Repositories added to enable Beryl\r\ndeb http://www.beerorkid.com/compiz
  dapper main aiglx\r\ndeb http://media.blutkind.org/xgl/ dapper main aiglx\r\n</code>\r\n"
categories:
- ubuntu
layout: story
author: kecsi
title: Compiz frissités Berylre Ubuntu Dapper alatt
created: 1160566034
---
Tegnap kíváncsiságból feltelepítettem a <a href="http://www.beryl-project.org/">Beryl-t</a> lecserélve az eddigi <a href="/xgl_compiz">compiz</a> ablakmenedzserem.

Itt találtam segítséget: <a href="http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL">1</a>, <a href="http://ubuntuforums.org/showthread.php?t=268036">2</a>

A dolog meglehetősen egyszerű volt:
Egyenlőre az X szerverem békén hagytam (XGL-t), csak a beryl csomagokat telepítettem fel.
Először hozzáadtam a megfelelő csomag repot apt-hoz:
<code>
# Repositories added to enable Beryl
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
</code>
<!--break-->
Majd telepítettem a csomagokat:
<code>
wajig install beryl emerald-themes
</code>
ez egyúttal el is távolította a compiz csomagokat.

X session újraindítása után már nem indítottam el a compizt (nem is tudtam volna hisz nem volt feltelpítve) de elindítottam a berylt:
<code>
beryl-manager
</code>
Már működött is minden.

A tapasztalataim vegyesek:
 - lassabb
 - az eddigi compizzal is elégedett voltam, úgy érzem nem fogom kihasználni az újdonságait igazán.
 - de alapjában véve tetszik, de ha sok gondom lesz vele visszatérek compizra mert az stabilan működött.
