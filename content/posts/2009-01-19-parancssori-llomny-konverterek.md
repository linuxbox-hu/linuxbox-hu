---
author: kecsi
categories:
- linux
created: 1232375323
date: '2009-01-19T00:00:00Z'
excerpt: 'Ha unix és dos text állományok közt kell konvertálni akkor használhajuk a dos2unix, dos2unix, fromdos, todos egyszerű konvertáló eszközöket. De ha esetleg már UTF8-ra kell konvertálni akkor már szükségünk lehet egy kicsit komolyabb eszközre mint a recode nevű szoftver. Használatára egy példa: recode ISO-8859-1..UTF-8 test_file_to_utf8.txt'
title: Parancssori állomány konverterek
aliases:
- /node/582/
- /story/582/
---
Ha unix és dos text állományok közt kell konvertálni akkor használhajuk a 
<code>dos2unix, dos2unix, fromdos, todos</code> egyszerű konvertáló eszközöket.

De ha esetleg már UTF8-ra kell konvertálni akkor már szükségünk lehet egy kicsit komolyabb eszközre mint a <code>recode</code> nevű szoftver.
Használatára egy példa: <code>recode ISO-8859-1..UTF-8 test_file_to_utf8.txt</code>

A sysutils, tofrodos és recode nevű csomagokkal telepíthetőek a szoftverek debian alapú rendszereken.
