---
excerpt: "Akinek sokat kell nyomtatott szöveget szkennelnie és azokat visszaalakítani
  szerkeszthető szöveggé, az valószínűleg találkozott már a probléma különféle szoftveres
  megoldás nyújtotta lehetőségével.\r\n\r\n<img src=\"/files/ocr_test.png\" />\r\n\r\n<img
  src=\"/files/ocr_zoom.png\" />\r\n\r\nA <a href=\"http://jocr.sourceforge.net\">Gocr</a>
  nevű kisméretű parancssori program az említett problémára nyújt megoldást a nyílt
  forráskódú területről.\r\n\r"
categories: []
layout: blog
author: log69
title: Gocr - optikai karakterfelismerő szoftver
created: 1190738403
---
Akinek sokat kell nyomtatott szöveget szkennelnie és azokat visszaalakítani szerkeszthető szöveggé, az valószínűleg találkozott már a probléma különféle szoftveres megoldás nyújtotta lehetőségével.

<img src="/sites/default/files/ocr_test.png" />

<img src="/sites/default/files/ocr_zoom.png" />

A <a href="http://jocr.sourceforge.net">Gocr</a> nevű kisméretű parancssori program az említett problémára nyújt megoldást a nyílt forráskódú területről.

Kipróbáltam a fentebb látható képpel az alábbi módon egy viszonylag nagyon kicsi felbontású szövegre futtatva, és ehhez képest elég jó eredményt adott, esetemben egyetlen betűt tévesztve. Meg kell még említenem, hogy magyar ékezetes betűkkel ilyen kicsi felbontásban nem adott jó eredményt.
~$ gocr image.png
This is a testing phrase and the only purpose of all this here is
to demonstrate the optical charachter recognition soft_uare.

http://jocr.sourceforge.net
(a jocr név azért nem gocr, mert -mint ahogy a szerző írja- foglalt volt a név a regisztrációkor)
