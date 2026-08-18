---
author: log69
categories: []
created: 1190738403
date: '2007-09-25T00:00:00Z'
title: 'Gocr - optikai karakterfelismerő szoftver'
aliases:
- /blog/436/
- /node/436/
---
Akinek sokat kell nyomtatott szöveget szkennelnie és azokat visszaalakítani szerkeszthető szöveggé, az valószínűleg találkozott már a probléma különféle szoftveres megoldás nyújtotta lehetőségével.

![](/assets/img/posts/ocr_test.png)

![](/assets/img/posts/ocr_zoom.png)

A [Gocr](http://jocr.sourceforge.net) nevű kisméretű parancssori program az említett problémára nyújt megoldást a nyílt forráskódú területről.

Kipróbáltam a fentebb látható képpel az alábbi módon egy viszonylag nagyon kicsi felbontású szövegre futtatva, és ehhez képest elég jó eredményt adott, esetemben egyetlen betűt tévesztve. Meg kell még említenem, hogy magyar ékezetes betűkkel ilyen kicsi felbontásban nem adott jó eredményt.

```bash
~$ gocr image.png
This is a testing phrase and the only purpose of all this here is
to demonstrate the optical charachter recognition soft_uare.
```

<http://jocr.sourceforge.net>
(a jocr név azért nem gocr, mert -mint ahogy a szerző írja- foglalt volt a név a regisztrációkor)
