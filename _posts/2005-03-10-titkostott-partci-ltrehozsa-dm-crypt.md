---
excerpt: "A dolog lényege annyi, hogy egy titkosítási módszerrel és kulccsal vagy
  jelszóval létrehozunk egy virtuális eszközt amin keresztül használjuk a partíciónkat.\r\n\r\nMielőtt
  nekilátunk ellenőrizzük, hogy van-e <em>dmsetup</em> csomagunk telepítve és van-e
  <em>dm-crypt</em> kernel modulunk.\r\n"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Titkosított partíció létrehozása; dm-crypt
created: 1110484869
---
A dolog lényege annyi, hogy egy titkosítási módszerrel és kulccsal vagy jelszóval létrehozunk egy virtuális eszközt amin keresztül használjuk a partíciónkat.

Mielőtt nekilátunk ellenőrizzük, hogy van-e <em>dmsetup</em> csomagunk telepítve és van-e <em>dm-crypt</em> kernel modulunk.
<!--break-->
Ezután nekiugorhatunk:
Létrehozzuk az eszközt pl. így:

<strong>echo 0 `blockdev --getsize /dev/hda5` crypt aes-plain 0123456789abcdef0123456789abcdef 0 /dev/hda5 0 | dmsetup create volume1</strong>

Nem felejtjük megváltoztatni és elmenteni a kulcsnak szánt 32 bites számot, amivel a jövőben ismételgetni tudjuk a létrehozást és így használni tudjuk az adatokat.

pl. így:
<strong>echo 0 `blockdev --getsize /dev/hda5` crypt aes-plain `cat keyfile.mentes` 0 /dev/hda5 0 | dmsetup create volume1

mkfs.ext3 /dev/mapper/volume1

mount /dev/maper/volume1 /mnt
</strong>

További info <a href="http://hu.gentoo-wiki.com/BIZTONS%C3%81G_F%C3%A1jlrendszer_titkos%C3%ADt%C3%A1s">itt magyarul,</a> és <a href="http://www.saout.de/misc/dm-crypt/">itt angolul</a> plusz egy <a href="http://gentoo-wiki.com/HOWTO_dmcrypt"> jó howto szintén angolul</a> itt.
