---
author: Goosfrabaa
categories:
- linux
created: 1264633429
date: '2010-01-27T00:00:00Z'
excerpt: |
  Ha desktop környezettől független, mégis kényelmes módját keressük az MS Windows hálózat tallózásának akkor érdemes egy pillantást vetni a GTK2 alapú <a href="http://sourceforge.net/projects/g2sc">g2sc</a>-re és a parancssori <a href="http://smbnetfs.sourceforge.net/">smbnetfs</a> csomagra.
title: MS Windows megosztások tallózása
aliases:
- /node/655/
- /story/655/
---
Ha desktop környezettől független, mégis kényelmes módját keressük az MS Windows hálózat tallózásának akkor érdemes egy pillantást vetni a GTK2 alapú <a href="http://sourceforge.net/projects/g2sc">g2sc</a>-re és a parancssori <a href="http://smbnetfs.sourceforge.net/">smbnetfs</a> csomagra.
<!--break-->
Míg az előbbi "adja magát" az egyszerű felületnek köszönhetően, az utóbbiról érdemes néhány szót szólni:
a program egy fuse kiegészítés, azaz anélkül nem működik. Ha a megszokott módon szolgáltatásként indítjuk, akkor a /mnt/smbnet/ könyvtár alatt lesznek láthatók a gépek és megosztásaik. Egyszerű és nagyszerű.
