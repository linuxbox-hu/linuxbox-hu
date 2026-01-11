---
excerpt: "Ha egy AVI állományt DVD formátumra akarunk konvertálni a következő lépéseket
  érdemes követni:\r\n<code>mencoder -o finalmovie.avi -noidx -oac copy -ovc copy
  dvd.avi\r\nffmpeg -i finalmovie.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg\r\ndvdauthor
  --title -o dvd -f finalmovie.mpg\r\ndvdauthor -o dvd -T\r\nmkisofs -dvd-video -o
  dvd.iso dvd/</code>\r\nEzután a DVD-t egy közönséges asztali lejátszóval is le kéne
  tudjuk játszani.\r\n\r\nEllenkező irányba (dvd -> avi) konvertáláskor használható
  akár a <a href=\"http://handbrake.m0k.org>HandBrake</a> nevű alkalmazás is."
categories:
- x
layout: story
author: kecsi
title: AVI állomány DVD-re írása és fordítva
created: 1193143968
---
Ha egy AVI állományt DVD formátumra akarunk konvertálni a következő lépéseket érdemes követni:
<code>mencoder -o finalmovie.avi -noidx -oac copy -ovc copy dvd.avi
ffmpeg -i finalmovie.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg
dvdauthor --title -o dvd -f finalmovie.mpg
dvdauthor -o dvd -T
mkisofs -dvd-video -o dvd.iso dvd/</code>
Ezután a DVD-t egy közönséges asztali lejátszóval is le kéne tudjuk játszani.

Ellenkező irányba (dvd -> avi) konvertáláskor használható akár a <a href="http://handbrake.m0k.org>HandBrake</a> nevű alkalmazás is.
