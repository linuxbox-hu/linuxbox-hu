---
layout: post
title: "etckeeper: a /etc könyvtár git alatt"
date: 2026-08-08 09:00:00 +0000
categories: [linux, utils]
tags:
 - etckeeper
 - git
 - sysadmin
image:
  path: ../assets/img/logos/git-logo.png
---
Ha valaha módosítottál egy config fájlt a `/etc` alatt, aztán két hét múlva már nem emlékeztél mit és miért állítottál át - erre való az `etckeeper`.

Egyetlen csomag, ami a `/etc` könyvtárat automatikusan git repóba teszi, és minden csomagkezelő (apt/dnf/pacman) művelet előtt-után automatikusan commitol. Így minden változás nyomon követhető, visszaállítható, és összehasonlítható.

Telepítés Debian/Ubuntu-n:

```bash
sudo apt install etckeeper
```

Ennyi. A `/etc` már init-elve van git repóként, és a csomagkezelő hookjai automatikusan commitolnak minden `apt install`/`apt upgrade` körül.

Saját kézi változtatásnál érdemes commitolni:

```bash
sudo etckeeper commit "sshd_config: PermitRootLogin no"
```

Hasznos parancsok utólag:

```bash
# mi változott mostanában?
sudo git -C /etc log --oneline -20

# mikor és hogyan változott egy adott fájl?
sudo git -C /etc log -p /etc/ssh/sshd_config

# egy korábbi verzió visszaállítása
sudo git -C /etc checkout <commit> -- /etc/ssh/sshd_config
```

> Ha több gépet is Ansible-lel (vagy bármilyen más automatizálással) kezelünk, érdemes minden gépen bekapcsolni - így egy hibás automatizált változtatás után pontosan látszik mi változott és mikor.
{: .prompt-tip }

Kis, ingyenes biztonság: nem kell több, mint egy `apt install`, és a következő "miért nem működik már megint ez a config" pillanatban össze tudod hasonlítani a mostani és a régi állapotot.
