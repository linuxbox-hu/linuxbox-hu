---
author: kecsi
categories:
- x
created: 1193143968
date: '2007-10-23T00:00:00Z'
excerpt: |-
  Ha egy AVI állományt DVD formátumra akarunk konvertálni a következő lépéseket érdemes követni:
  <code>mencoder -o finalmovie.avi -noidx -oac copy -ovc copy dvd.avi
  ffmpeg -i finalmovie.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg
  dvdauthor --title -o dvd -f finalmovie.mpg
  dvdauthor -o dvd -T
  mkisofs -dvd-video -o dvd.iso dvd/</code>
  Ezután a DVD-t egy közönséges asztali lejátszóval is le kéne tudjuk játszani.
  
  Ellenkező irányba (dvd -> avi) konvertáláskor használható akár a <a href="http://handbrake.m0k.org>HandBrake</a> nevű alkalmazás is.
title: AVI állomány DVD-re írása és fordítva
---
Ha egy AVI állományt DVD formátumra akarunk konvertálni a következő lépéseket érdemes követni:
<code>mencoder -o finalmovie.avi -noidx -oac copy -ovc copy dvd.avi
ffmpeg -i finalmovie.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg
dvdauthor --title -o dvd -f finalmovie.mpg
dvdauthor -o dvd -T
mkisofs -dvd-video -o dvd.iso dvd/</code>
Ezután a DVD-t egy közönséges asztali lejátszóval is le kéne tudjuk játszani.

Ellenkező irányba (dvd -> avi) konvertáláskor használható akár a <a href="http://handbrake.m0k.org>HandBrake</a> nevű alkalmazás is.
