---
author: kecsi
categories:
- linux
created: 1107211302
date: '2005-01-31T00:00:00Z'
description: 'Aktualis mailsor: mailq. Levél kivétele a sorbol: exim -Mrm . A reject/retry adatbázisok törlése: exim_tidydb. Mailq újrafeldolgozás: exim -qf / exim -qff.'
title: exim mailsor kezelés
aliases:
- /node/2/
- /story/2/
---
Aktualis mailsor:
```bash
mailq
```

Levél kivétele a sorbol:
```bash
exim -Mrm 175TfP-0004uA-00 17CTav-0007R5-00
```

A reject/retry azaz kézbesíthetetlen címek adatbázisának törlése:
```bash
exim_tidydb -t 0d /var/spool/exim/ reject
exim_tidydb -t 0d /var/spool/exim/ retry
```

Mailq újrafeldolgozás:
```bash
exim -qf
exim -qff
```
