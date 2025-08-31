---
excerpt: "Egy mentési módszer:\r\n <strong>pg_dump -c -d -f backup_file.dmp -F p -O
  dbnev</strong>\r\n\r\nLehet egyszerre tömöríteni is:\r\n <strong>pg_dump -c -d -F
  p -O dbnev | bzip2 > dbmentes.dmp.bz2</strong>"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: postgresql adatbázis dump
created: 1107351636
---
Egy mentési módszer:
 <strong>pg_dump -c -d -f backup_file.dmp -F p -O dbnev</strong>

Lehet egyszerre tömöríteni is:
 <strong>pg_dump -c -d -F p -O dbnev | bzip2 > dbmentes.dmp.bz2</strong>
