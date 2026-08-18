---
author: batyu
categories: []
created: 1263659722
date: '2010-01-16T00:00:00Z'
description: 'RGBimg2CMYKtiff: Nos, sokadik próbálgatásra sikerült egy működő változatot eszkábálni, csatolt file-ban megtalálható. Bár egyelőre csak monitorokon tudtam ellenőrizni, de gyakorlatilag ugyanazt az eredményt adja, mint a krita - csak pár 10 másodperc alatt, guira várakozás nélkül. Ja, és ugyanaz mogrify-ra, több fájl egyszerre feldolgozására.\r'
title: multimédia scriptek V.
aliases:
- /blog/653/
- /node/653/
---
RGBimg2CMYKtiff: Nos, sokadik próbálgatásra sikerült egy működő változatot eszkábálni, csatolt file-ban megtalálható. Bár egyelőre csak monitorokon tudtam ellenőrizni, de gyakorlatilag ugyanazt az eredményt adja, mint a krita - csak pár 10 másodperc alatt, guira várakozás nélkül. Ja, és ugyanaz mogrify-ra, több fájl egyszerre feldolgozására.
- egy csekély probléma, ami megoldásra vár: alfa csatornát tartalmazó képekből (pl png) megtartja az alfa csatornát a tiff-ben is -> emiatt nem pakolható a kapott tiff a tiff2pdf-el közvetlen pdf-be. Scribus dev viszont kezeli, X-1a-ra és ps-re se dob hibát a preflight, ám a kapott pdf nem teljesen az, amit várnánk, az átlátszóság a háttér előtt eltűnik, teliszínes objektumokon megmarad.


