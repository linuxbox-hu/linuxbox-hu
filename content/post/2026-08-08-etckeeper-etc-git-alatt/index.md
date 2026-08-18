---
author: kecsi
categories:
- linux
- utils
date: '2026-08-08T09:00:00Z'
image:
  path: git-logo.png
  small: true
tags:
- etckeeper
- git
- sysadmin
title: 'etckeeper: a /etc könyvtár git verzió követése'
---
Az `etckeeper` eszközzel, könnyedén követhetjük minden konfigurációs állományunnk módosítását az `/etc` mappában.

A csomag telepítéskor automatikusan git verzió követés alá helyezi az `/etc` könyvtárunkat. 
Minden csomagkezelő (apt/dnf/pacman) művelet előtt-után automatikusan könyveli a változásokat "hook"-ok segíségével.
Minden változás nyomon követhető, visszaállítható, és összehasonlítható.

Telepítés Debian/Ubuntu-n:

```bash
sudo apt install etckeeper
```

Saját kézi config változtatásnál érdemes commitolni, pl.:

```bash
sudo etckeeper commit "sshd_config: PermitRootLogin no"
```

Hasznos parancsok használathoz:

```bash
# mi változott mostanában?
sudo git -C /etc log --oneline -20

# mikor és hogyan változott egy adott fájl?
sudo git -C /etc log -p /etc/ssh/sshd_config

# egy korábbi verzió visszaállítása
sudo git -C /etc checkout <commit> -- /etc/ssh/sshd_config
```

> akár több gépre is bevezethetjük Ansible-lel (vagy hasonló "configuration management" eszközzel).
