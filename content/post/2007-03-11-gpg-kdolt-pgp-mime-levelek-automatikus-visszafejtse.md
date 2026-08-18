---
author: szimszon
categories:
- linux
created: 1173630397
date: '2007-03-11T00:00:00Z'
description: 'Ez egy olyan script, ami automatikusan kicsomagolja a megfelelő gpg/pgp
  kulccsal titkosított és aláírt leveleket.'
title: GPG kódolt (pgp-mime) levelek automatikus visszafejtése
aliases:
- /node/335/
- /story/335/
---
[mail_gpg_extract.py](http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2) [.asc](http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2.asc)

Ez egy olyan script, ami automatikusan kicsomagolja a megfelelő *gpg/pgp* kulccsal titkosított és aláírt leveleket.

Felhasználható például olyan esetekben, amikor egy szervernek hiteles forrásból érkező utasítást/szöveget/fájlt szeretnénk levél útján eljuttatni.

A script önmagában a következőt teszi:

- az alapértelmezett bemenetről érkező levelet fogadja és ,,pgp-encrypted'' Content-type-ot keres benn.
- ha nem talál, akkor a levelet (egy naplóbejegyzés után) eldobja
- a gpg titkosított és aláírt levelet visszafejti és
- egy a parancssorban megadott könyvtárba kitömöríti
- így tetszőleges program elvégezheti a további műveleteket

A könyvtár struktúrája ahova a visszafejtett levél el lesz mentve:

- minden levél külön könyvtárba kerül, ennek a könyvtárnak a neve a levél érkezésének időbéllyege (time.time())
- a levélhez tartozó könyvtárba a könyvtár nevével megegyező időbélyeg nevű fájlba belekerül a:

```text
------- cut -------
From: <az eredeti levél feladója>
Subject: <az eredeti levél tárgya>
<a gpg program kimenete - milyen kulccsal titkosították és írták alá a levelet>
------- cut -------
```

- a könyvtár további tartalma a visszafejtett levél tartalma és fájljai

*A program nem végez semmiféle rekurzív levél kibontást vagy fájl kitömörítést!*

## Előfeltételek

A program *Python2.4*-gyel lett tesztelve és az alábbi modulokat használja:

- email
- mimetypes
- sys
- os
- GnuPGInterface
- re
- time
- getopt
- tempfile
- segito

## Telepítés

Másoljuk a *mail_gpg_extract.py* scriptet és *segito.py* modult bárhova egy közös könyvtárba.

## Program használata

```bash
<mail az alapért.bemenetrol> | mail_exec.py -d <könyvtár> [-p <jelmondat>]
```

`könyvtár` - a könyvtár ahova a visszafejtett levelek mentésre kerülnek
`jelmondat` - gpg/pgp kulcshoz tartozó jelmondat

A jelmondatot három féle képpen lehet megadni:

- a programban: `parameters.set_passphrase('<jelmondat>')`
- paraméterrel: -p `<jelmondat>`
- környezeti válozóban: `export PASSPHRASE="<jelmondat>"`

## Példa .procmailrc

```bash
-------------- cut ----------------
MAIL_GPG_EXTRACT="/home/robot/bin/mail_gpg_extract.py"
QUEUE_GPGMAIL="/home/robot/.queue_gpgmail"
:0
* ^To.*gpgmail
| ${MAIL_GPG_EXTRACT} -d ${QUEUE_GPGMAIL}
-------------- cut ----------------
```

- A példa működéséhez létre kell hozni egy ,,robot'' nevű felhasználót, akinek a jogaival fog futni a ,,mail_gpg_extract.py'' script.
- A robot saját könyvtárán belül a ,,bin'' könyvtárba másoljuk a scriptet és a segito.py modult.
- Továbbá szükség van a robot felhasználó által beállítani a gnupg/pgp programokat, és a kulcs cserét ugyanúgy megtenni, mintha elő személlyel szeretnénk gpg/pgp-vel kódoltan és aláírtan levelezni.
- Célszerű ha a ,,robot'' felhasználó csak azokat a gpg/pgp kulcsokat ismeri akiktől elfogadhat levelet.

## Garancia

A programmal kapcsolatban nem vállalok semmiféle garanciát. Bízom benne, hogy a script azt csinálja és csak azt amire megírtam :)

## Licenc

GPLv2

## Végszó

Nem hiszem, hogy a script aktívan fejlesztve lesz, minden hibajavítást, észrevételt szívesen veszek!

*Mindenkinek jó munkát!*
