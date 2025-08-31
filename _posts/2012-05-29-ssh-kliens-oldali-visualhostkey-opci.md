---
excerpt: "Csatlakozás egy távoli szerverre tehető biztonságosabbá a SSH 5.1 óta létező
  VisualHostKey kliens oldali opció használatával. \r\nTudni illik ez az opció egy
  a kulcs ujlenyomatának egy generált képét jeleníti meg csatlakozáskor. Ami memorizálható.
  Így ha valaki \"man in the middle\" támadással akarja megszerezni az adatainkat
  előfordulhat, hogy könnyebben észleljük a változást...\r\n\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: ssh kliens oldali VisualHostKey opció
created: 1338300332
---
Csatlakozás egy távoli szerverre tehető biztonságosabbá a SSH 5.1 óta létező VisualHostKey kliens oldali opció használatával. 
Tudni illik ez az opció egy a kulcs ujlenyomatának egy generált képét jeleníti meg csatlakozáskor. Ami memorizálható. Így ha valaki "man in the middle" támadással akarja megszerezni az adatainkat előfordulhat, hogy könnyebben észleljük a változást...

Parancssorból így használható:
</code>
ssh -o VisualHostKey=yes user@host
</code>

Avagy ha be akarjuk kapcsolni véglegesen megadott szerverekhez vagy akár minden szerverre akkor az .ssh/config állományunkhoz kell hozzáadnunk a következő két sort:
</code>
Host *
        VisualHostKey           yes
</code>
Bekapcsolás után igy fog kinézni a kapcsolódás:
<pre>
[me@server]:~> ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 11:2e:1e:17:ea:2d:c1:fb:4d:16:11:b3:a2:06:11:11.
+--[ RSA 2048]----+
|    .            |
|   . E           |
|  .   .          |
| . . . .         |
|... o + S        |
|. o. = .         |
|.  o+ o          |
|..=o *           |
|+o+*+ .          |
+-----------------+
</pre>
