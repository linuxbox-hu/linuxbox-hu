---
author: bAndie91
categories: []
created: 1256422760
date: '2009-10-24T00:00:00Z'
title: SSH bejelentkezés jelszó nélkül
---
Ha jelszó törésrõl szeretnél olvasni, ajánlom John the Ripper oldalát. Most egyszerũen a DSA/RSA kulcsok segítségével történõ ssh-zásról írok.

Ezt a rövidített howto-t a http://wiki.lme.hu/lmewiki/index.php/SSH alapján írtam.
Rendelkezünk OpenSSH szerverrel es klienssel.
A kulcsgenerálasnál (ssh-keygen) hagyjuk az alapértelmezettet:
*.pub az id_dsa.pub és az id_rsa.pub fájlokat takarja.
Kövessük el az alábbi parancsokat.
$ ssh-keygen -t dsa
$ ssh-keygen -t rsa
$ cat ~/.ssh/*.pub > authorized_keys
$ scp authorized_keys USER@HOST:/home/USER/.ssh/authorized_keys

Ahol a HOST a távoli szerver, USER az ottani login nevünk.
Ha további munkaállomások publikus dsa és rsa kulcsait akarjuk az jelszó nelkül beengedendõ
kulcsok küzé tenni, fũzzük ezeket hozzá a ~/.ssh/authorized_keys fájlhoz.
(Ha más az alapértelmezett beállítás, az /etc/ssh/ssh_config fájlból kideríthetjük.)
