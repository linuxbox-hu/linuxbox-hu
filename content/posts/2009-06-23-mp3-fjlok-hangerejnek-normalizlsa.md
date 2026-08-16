---
author: Goosfrabaa
categories:
- linux
created: 1245753558
date: '2009-06-23T00:00:00Z'
excerpt: |
  Rengeteg mp3 fájlod van különböző hangerővel? A megoldás egy parancssori alkalmazás, ami veszteségmentes módon normalizálja az állományokat.
title: Mp3 fájlok hangerejének normalizálása
---
Rengeteg mp3 fájlod van különböző hangerővel? A megoldás egy parancssori alkalmazás, ami veszteségmentes módon normalizálja az állományokat.
<!--break-->
A multiplatformos <strong>mp3gain</strong> a legtöbb disztribúcióban valószínűleg benne van, de elvileg letölthető <a href="http://mp3gain.sourceforge.net">innen</a> is (a zip fájlt kell letölteni és fordítani).

A különböző leírások szerint a legegyszerűbb megoldás egy könyvtár összes fájljának normalizálásához:
</code>mp3gain -r -k *mp3</code>

Úgy tűnik APEv2 formájú TAG esetén előfordulhat, hogy eltűnnek a <a href="http://mp3gain.sourceforge.net/faq.php">bejegyzések.</a>

Aki nem tud élni grafikus felület nélkül, az nézze meg <a href="http://sourceforge.net/projects/easymp3gain">ezt</a>.

<a href="http://www.linux.com/archive/articles/59957">További tippek</a>.

Aki pedig <strong>ogg</strong> fájlokkal rendelkezik sincs hátrányban, mert nekik ott a <a href="http://www.sjeng.org/vorbisgain.html">VorbisGain</a>, ami repokban is megtalálható.
