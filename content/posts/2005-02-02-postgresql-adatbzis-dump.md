---
author: kecsi
categories:
- linux
created: 1107351636
date: '2005-02-02T00:00:00Z'
excerpt: 'Egy mentési módszer: pg_dump -c -d -f backup_file.dmp -F p -O dbnev Lehet egyszerre tömöríteni is: pg_dump -c -d -F p -O dbnev | bzip2 > dbmentes.dmp.bz2'
title: postgresql adatbázis dump
aliases:
- /node/16/
- /story/16/
---
Egy mentési módszer:
 `pg_dump -c -d -f backup_file.dmp -F p -O dbnev`

Lehet egyszerre tömöríteni is:
 `pg_dump -c -d -F p -O dbnev | bzip2 > dbmentes.dmp.bz2`
