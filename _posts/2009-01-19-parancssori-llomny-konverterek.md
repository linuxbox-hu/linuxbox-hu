---
excerpt: "Ha unix és dos text állományok közt kell konvertálni akkor használhajuk
  a \r\n<code>dos2unix, dos2unix, fromdos, todos</code> egyszerű konvertáló eszközöket.\r\n\r\nDe
  ha esetleg már UTF8-ra kell konvertálni akkor már szükségünk lehet egy kicsit komolyabb
  eszközre mint a <code>recode</code> nevű szoftver.\r\nHasználatára egy példa: <code>recode
  ISO-8859-1..UTF-8 test_file_to_utf8.txt</code>\r\n\r"
categories:
- linux
layout: story
author: kecsi
title: Parancssori állomány konverterek
created: 1232375323
---
Ha unix és dos text állományok közt kell konvertálni akkor használhajuk a 
<code>dos2unix, dos2unix, fromdos, todos</code> egyszerű konvertáló eszközöket.

De ha esetleg már UTF8-ra kell konvertálni akkor már szükségünk lehet egy kicsit komolyabb eszközre mint a <code>recode</code> nevű szoftver.
Használatára egy példa: <code>recode ISO-8859-1..UTF-8 test_file_to_utf8.txt</code>

A sysutils, tofrodos és recode nevű csomagokkal telepíthetőek a szoftverek debian alapú rendszereken.
