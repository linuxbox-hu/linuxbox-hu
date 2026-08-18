---
author: kecsi
categories:
- ubuntu
created: 1200510822
date: '2008-01-16T00:00:00Z'
description: 'Ha valaki sokat használja a Redhat parancssori "service" utasítását talán a debian alapú Ubuntuban is szívesen látná ezt az utasítást. Mikor kiadjuk a service utasítást a bemutatott szolgáltatás telepítése előtt rendszerünk okosan tájékoztat, hogy telepítsük fel a sysvconfig csomagot ami tartalmazza ezt a kis szkriptet. Szóval ne habozzunk: sudo aptitude install sysvconfig'
title: '"service" szkript hozzáférhető Ubuntu 7.10-n'
aliases:
- /node/468/
- /story/468/
---
Ha valaki sokat használja a Redhat parancssori "service" utasítását talán a debian alapú Ubuntuban is szívesen látná ezt az utasítást. Mikor kiadjuk a service utasítást a bemutatott szolgáltatás telepítése előtt rendszerünk okosan tájékoztat, hogy telepítsük fel a sysvconfig csomagot ami tartalmazza ezt a kis szkriptet. Szóval ne habozzunk: <code>sudo aptitude install sysvconfig</code>
<!--break-->
Mit tudunk vele csinálni, mire is való ez? Hasonlókra:
<code>
    sudo service apache2 restart
    sudo service ntpd stop
    sudo service network restart
</code>

<a href="http://ubuntu-tutorials.com/2007/11/13/service-tool-available-on-ubuntu-710/">Forrás</a>
