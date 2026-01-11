---
excerpt: "Az imagemagick csomag convert utasitását használjuk ebben az apró bash shell
  scriptben jpeg állományok gifre konvertálára:\r\n<code>\r\nfor x in $(ls)\r\ndo\r\n
  \ convert $x ${x%.jpg}.gif\r\ndone\r\n</code>\r\n\r\navagy parancssorban egy bash
  for ciklussal  egy sorban bmpt jpgre:\r\n\r\n<code>for x in $(ls *.bmp); do convert
  $x ${x%.bmp}.jpg; done</code>"
categories:
- linux
layout: story
author: kecsi
title: batch kép konvertálás
created: 1143625446
---
Az imagemagick csomag convert utasitását használjuk ebben az apró bash shell scriptben jpeg állományok gifre konvertálára:
<code>
for x in $(ls)
do
  convert $x ${x%.jpg}.gif
done
</code>

avagy parancssorban egy bash for ciklussal  egy sorban bmpt jpgre:

<code>for x in $(ls *.bmp); do convert $x ${x%.bmp}.jpg; done</code>
