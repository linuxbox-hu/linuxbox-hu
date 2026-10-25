---
author: kecsi
categories:
- linux
- utils
date: '2026-10-25T18:00:00Z'
tags:
- chrony
- ntp
- debian
- ansible
title: 'chrony: időszinkron Debian 13 (Trixie) alatt, az ntp helyett'
---
A Debian 13-ból (Trixie) kikerült az eddig klasszikusként használt `ntp` csomag, az `apt install ntp` már nem talál telepíthető verziót. Szervereken a `chrony` a kézenfekvő csere szerintem: bár az alapértelmezett a `systemd-timesyncd` de ez csak egyszerű SNTP kliens, a `chrony` viszont részletes állapotot mutat, és szükség esetén másoknak is ki tud szolgálni időt.

Maga az apt is két helyettesítőt ajánl az `ntp` helyett (`openntpd`, `ntpsec`). Az `ntpsec` az eredeti NTP kódbázis megerősített, biztonságra hangolt változata, ugyanúgy `ntp.conf` és `ntpq` jár hozzá, támogatja az NTS-t is, és teljesen jó választás, ha a megszokott `ntpd` környezetet akarjuk megtartani. Az `openntpd` az OpenBSD kicsi, jogosultság-szétválasztást használó megvalósítása, az NTP protokollnak viszont csak egy részhalmazát tudja. Én mégis a `chrony`-t választom: az `ntpsec` a Python 3-at is behúzza, a `chrony` nem, a `chronyc` kimenete pedig könnyebben olvasható. Ráadásul a saját gépeimen mindenhol ugyanaz fut, így elég egyetlen szerepkör.

A harmadik lehetőség az `ntpd-rs`, egy Rust nyelven írt, NTS-t támogató megvalósítás, a Trixie-ben is megtalálható. Ígéretes projekt, de a Debian csomagja az 1.4.0-s verzió, miközben upstream már az 1.9.0-nál tart, és a Debian stabil kiadása általában csak javításokat kap, új verziót nem. Szerverre egyelőre még várnék vele.

Telepítés:

```bash
sudo apt install chrony
```

Az apt a telepítéskor leveszi a `systemd-timesyncd`-t.

Használat:

```bash
# mennyire pontos most az óra?
chronyc tracking

# honnan szinkronizál?
chronyc sources -v
```

A `sources` kimenetében a `^*` a most használt szervert jelöli, a `^+` a használható tartalékot, a `^?` az elérhetetlent. A `Reach` oszlopban a `377` azt jelenti, hogy az utolsó nyolc lekérdezés mind sikerült.

Lekérdezéshez nem kell sudo, de ha módosítani próbálunk a rendszeridőn, akkor igen (nélküle `501 Not authorised` hibát kapunk):

```bash
chronyc sourcestats     # források statisztikája (eltérés, szórás)
chronyc activity        # hány forrás elérhető, hány nem
sudo chronyc makestep   # azonnali órakorrekció, ha nagyon elmászott
chronyc waitsync 30     # vár a szinkronig, szkriptekbe jó
```

Otthoni hálón érdemes a saját routert tenni elsőnek (pl. MikroTik, értelem szerűen, ott be kell kapcsolni az NTP szervert előzőleg), a publikus szerverek pedig menjenek tartaléknak:

```bash
# /etc/chrony/chrony.conf
server 192.168.1.1 iburst prefer
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst

makestep 1.0 3
rtcsync
```

Az `iburst` gyorsítja az első szinkront, a `prefer` a routert részesíti előnyben, a `makestep 1.0 3` pedig megengedi, hogy az óra az első három frissítésnél ugorjon, ha több mint egy másodperccel tér el.

A fentiek automatizálására Ansible-t is lehet használni. 
Pl. a homelab repo [`configure_ntp`](https://github.com/kecsi-san/homelab/tree/main/roles/configure_ntp) erre való: leállítja a `systemd-timesyncd`-t, telepíti a `chrony`-t, a fenti konfigot sablonból teszi fel, és újraindítja a szolgáltatást, ha változott.
