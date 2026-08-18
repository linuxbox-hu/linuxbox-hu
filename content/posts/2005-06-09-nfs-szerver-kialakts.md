---
author: kecsi
categories:
- linux
created: 1118306675
date: '2005-06-09T00:00:00Z'
excerpt: 'A szerveren telepítsük fel a két szükséges szoftvert: portmapot és nfs-kernel-servert . Kernel támogatás is legyen. Majd konfiguráljuk be. # /etc/exports: the access control list for filesystems which may be exported # to NFS clients. See exports(5). /exportnev 152.66.X.X(rw,sync,no_root_squash) A rw - írást biztosít; synvc - működési típus; no_root_squash - rootnak is engedi mindezt. Kliens oldalra is kell a portmap! Aztán mehet a mount: mount -t nfs gepnev:/exportnev /mountpont'
title: nfs szerver kialakítás
aliases:
- /node/78/
- /story/78/
---
A szerveren telepítsük fel a két szükséges szoftvert: `portmapot és nfs-kernel-servert`. Kernel támogatás is legyen. Majd konfiguráljuk be.

```text
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/exportnev            152.66.X.X(rw,sync,no_root_squash)
```

A rw - írást biztosít; synvc - működési típus; no_root_squash - rootnak is engedi mindezt.

**Kliens oldalra is kell a portmap!** Aztán mehet a mount: `mount -t nfs gepnev:/exportnev /mountpont`

