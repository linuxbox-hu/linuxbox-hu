---
author: szimszon
categories:
- linux
created: 1147687053
date: '2006-05-15T00:00:00Z'
excerpt: |
  nem kell elkeseredni, mert létezik egy okos kis eszköz, melynek neve:
  
  <strong>exiftags</strong>
  
  <a href="http://johnst.org/sw/exiftags/">http://johnst.org/sw/exiftags/</a>
title: Ha utólag vesszük észre, hogy  a kameránk órája rosszul jár...
aliases:
- /node/157/
- /story/157/
---
nem kell elkeseredni, mert létezik egy okos kis eszköz, melynek neve:

<strong>exiftags</strong>

<a href="http://johnst.org/sw/exiftags/">http://johnst.org/sw/exiftags/</a>
<!--break-->

Csak egy példa a <a href="http://johnst.org/sw/exiftags/exiftime.1.html">http://johnst.org/sw/exiftags/exiftime.1.html</a> oldalról:

<strong>exiftime -v+5d -v-7M -fw -tg *.jpg</strong>

Ez a parancs átállítja a dátumot <em>+5</em> nappal és az időt visszaállítja <em>7</em> perccel, és az új értékeket visszaírja az <strong>Elkészült</strong> (Generated) mezőbe, mindezt kérdés nélkül teszi azokon a fájlokon amire illeszkedik a <em>*.jpg</em>.

A kimenet így néz ki:

<code>
example1.jpg:
Image Generated: 2003:09:12 17:05:37 -> 2003:09:17 16:58:37

example2.jpg:
Image Generated: 2004:01:22 17:07:02 -> 2004:01:27 17:00:02
</code>
