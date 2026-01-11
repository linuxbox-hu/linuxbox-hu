---
excerpt: "Remélem a következõ project-nek is helye van a box-ban.\r\nKészítek pár
  unix-szerû parancsfájlt, hogy win-es környezetben is lehessen közel hasonló szintaxissal
  elérni a hasonló, windows-os mûveleteket. \r"
categories: []
layout: blog
author: bAndie91
title: Unix-like Batch
created: 1251126858
---
Remélem a következõ project-nek is helye van a box-ban.
Készítek pár unix-szerû parancsfájlt, hogy win-es környezetben is lehessen közel hasonló szintaxissal elérni a hasonló, windows-os mûveleteket. 
Úgy tudom még nincs ilyen. Van ugyan a Cygwin, amit magam is használok, de az binárisokat használ. Ezek tiszta .bat-alapúak, csak néhány alapértelmezett .exe-t igényelnek (net, ipconfig, findstr, fsutil, ...). Nincs meg mindegyik SP nélkül, azokat vajon feltehetem (jogi szempontból) nyilvános helyre?
Igaz, a bat parancsfájlokkal nem kifejezetten lehet idiot-proof scripteket írni (lehet, h ezért bináris a legtöbb win-es commandline util?), ezért WITHOUT ANY WARRANTY.
Többek közt ezek már elég pofásak: {mount,ln,passwd,sudo}.bat
E lista késõbb bõvülni fog.
Aki még nem firkált bat-okat, csak szükség esetén tegye, a shellscript-elés hatékonyabb.
Teszterek véleményét várom.

Innen letölthetõ:
http://www.freeweb.hu/bandie91/pub/?t=2&dir=/programms/UnixLikeBatch
Az összes:
http://www.freeweb.hu/bandie91/pub/download.php?get=/programms/UnixLikeBatch/ALL.zip&back=/bandie91/pub/%3Ft%3D2%26dir=/programms/UnixLikeBatch
