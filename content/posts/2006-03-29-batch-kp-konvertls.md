---
author: kecsi
categories:
- linux
created: 1143625446
date: '2006-03-29T00:00:00Z'
excerpt: |-
  Az imagemagick csomag convert utasitását használjuk ebben az apró bash shell scriptben jpeg állományok gifre konvertálára:
  <code>
  for x in $(ls)
  do
    convert $x ${x%.jpg}.gif
  done
  </code>
  
  avagy parancssorban egy bash for ciklussal  egy sorban bmpt jpgre:
  
  <code>for x in $(ls *.bmp); do convert $x ${x%.bmp}.jpg; done</code>
title: batch kép konvertálás
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
