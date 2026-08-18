---
author: kecsi
categories:
- debian
created: 1123015652
date: '2005-08-02T00:00:00Z'
excerpt: 'Hm, az imént két perc alatt alatt sikerült hozzáférnem 2,4 G backup tárhelyhez
  ingyen! Íme a parancsok, amiket használtam a rendszeremen.'
title: gmail tárhely felcsatolása; gmailfs
aliases:
- /node/91/
- /story/91/
---
Hm, az imént két perc alatt alatt sikerült hozzáférnem 2,4 G backup tárhelyhez ingyen!
Íme a parancsok, amiket használtam a rendszeremen.

```bash
[18.][kecsi@linuxbox]:~>  mkdir google
[19.][kecsi@linuxbox]:~>  sudo apt-get install gmailfs
[20.][kecsi@linuxbox]:~>  sudo module-assistant auto-install fuse-source
[21.][kecsi@linuxbox]:~>  sudo mount -t gmailfs none /home/kecsi/google/ -o username=<a_te_hozzaferesed@gmail.com>,password=<a_te_jelszavad>,fsname=<a_te_kulcsod>
```
<!--break-->
Egy kis magyarázat:
- 18-19-hez ugye nem kell magyarázat.
- 20-as parancs letölti a fuse kernel modul forrást a gépedre, lefordítja, és feltölti azt. Ha nem <a href="http://linuxbox.hu/debkernel">debiános módon fordított kerneled</a> van, lehetnek vele problámáid... a lényeg, h fuse modult kell készítened. Nálam ez egy sor :D
- 21-es parancs végzi a tényleges felcsatolást, ahol szükséges egy gmail hozzáférés és egy titkosító kulcs.

Amennyiben ténylegesen állomáyokat másoltok a filerendszerre és megnézitek a webfelületen a leveleket, érdekes állományokat fogtok látni. Ne töröljétek le őket, mert akkor oda a mentés..:)
