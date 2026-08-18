---
author: kecsi
categories:
- linux
created: 1107213963
date: '2005-01-31T00:00:00Z'
description: 'root partició másolása: cd /; find -print0 -mount | cpio -p -0 -d -m -u /masikparticio vagy: arhiv készítés: find -print0 -mount|cpio -o -0 -O arhiv.cpio arhivból visszaállítás: cpio -i -m -d -u -I arhiv.cpio'
title: partició másolás, arhiválás cpio-val
aliases:
- /node/7/
- /story/7/
- /cpio
---
root partició másolása:
`cd /; find -print0 -mount | cpio -p -0 -d -m -u /masikparticio`

vagy:
- arhiv készítés: `find -print0 -mount|cpio -o -0 -O arhiv.cpio`
- arhivból visszaállítás: `cpio -i -m -d -u -I arhiv.cpio`
