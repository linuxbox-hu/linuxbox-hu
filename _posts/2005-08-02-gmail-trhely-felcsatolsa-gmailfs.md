---
excerpt: "Hm, az imént két perc alatt alatt sikerült hozzáférnem 2,4 G backup tárhelyhez
  ingyen!\r\nÍme a parancsok, amiket használtam a rendszeremen.\r\n\r\n<pre>[18.][kecsi@linuxbox]:~>
  \ mkdir google\r\n[19.][kecsi@linuxbox]:~>  sudo apt-get install gmailfs\r\n[20.][kecsi@linuxbox]:~>
  \ sudo module-assistant auto-install fuse-source\r\n[21.][kecsi@linuxbox]:~>  sudo
  mount -t gmailfs none /home/kecsi/google/ -o username=<em>a_te_hozzaferesed@gmail.com</em>,password=<em>a_te_jelszavad</em>,fsname=<em>a_te_kulcsod</em></pre>\r\n"
categories:
- debian
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: gmail tárhely felcsatolása; gmailfs
created: 1123015652
---
Hm, az imént két perc alatt alatt sikerült hozzáférnem 2,4 G backup tárhelyhez ingyen!
Íme a parancsok, amiket használtam a rendszeremen.

<pre>[18.][kecsi@linuxbox]:~>  mkdir google
[19.][kecsi@linuxbox]:~>  sudo apt-get install gmailfs
[20.][kecsi@linuxbox]:~>  sudo module-assistant auto-install fuse-source
[21.][kecsi@linuxbox]:~>  sudo mount -t gmailfs none /home/kecsi/google/ -o username=<em>a_te_hozzaferesed@gmail.com</em>,password=<em>a_te_jelszavad</em>,fsname=<em>a_te_kulcsod</em></pre>
<!--break-->
Egy kis magyarázat:
- 18-19-hez ugye nem kell magyarázat.
- 20-as parancs letölti a fuse kernel modul forrást a gépedre, lefordítja, és feltölti azt. Ha nem <a href="http://linuxbox.hu/debkernel">debiános módon fordított kerneled</a> van, lehetnek vele problámáid... a lényeg, h fuse modult kell készítened. Nálam ez egy sor :D
- 21-es parancs végzi a tényleges felcsatolást, ahol szükséges egy gmail hozzáférés és egy titkosító kulcs.

Amennyiben ténylegesen állomáyokat másoltok a filerendszerre és megnézitek a webfelületen a leveleket, érdekes állományokat fogtok látni. Ne töröljétek le őket, mert akkor oda a mentés..:)
