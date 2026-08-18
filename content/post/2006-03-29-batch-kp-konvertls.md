---
author: kecsi
categories:
- linux
created: 1143625446
date: '2006-03-29T00:00:00Z'
description: 'Az imagemagick csomag convert utasitását használjuk ebben az apró bash shell scriptben jpeg állományok gifre konvertálára: for x in $(ls) do convert $x ${x%.jpg}.gif done avagy parancssorban egy bash for ciklussal egy sorban bmpt jpgre: for x in $(ls *.bmp); do convert $x ${x%.bmp}.jpg; done'
title: batch kép konvertálás
aliases:
- /node/141/
- /story/141/
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
