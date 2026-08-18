---
author: kecsi
categories:
- linux
created: 1137058446
date: '2006-01-12T00:00:00Z'
description: Wajig mindenféle műveletre képes ami szóba kerülhet csomagokkal, démonokkal
  kapcsolatban.
title: 'wajig - minden egyben csomagkezelő'
aliases:
- /node/120/
- /story/120/
---
Wajig mindenféle műveletre képes ami szóba kerülhet csomagokkal, démonokkal kapcsolatban.
Íme a teljes JIG utasítás készlet:

```text
 addcdrom          CD-ROM hozzáadás a csomagok forrásaihoz
 auto-alts         alternatív csomag megmutatása (prioritások használatával)
 auto-clean        etöltött és telepített csomagok törlése az átmenti tárból
 auto-download     frissülő csomagok letöltése majd telepítése
 auto-install      telepítés interaktivitás nélkül
 available         hozzáférhető és telepíthető összes csomag listája
 bug               jelentett hibák ellenőrzése a Debian hibajelentő rendszerben
 build             letölti a forrás csomagot és deban csomagot készít
 build-depend      letölti a megadott csomag függőségeit forrásból és elkészíti a csomagokat
 changelog         letölti az legutolsó változások listáját a csomaghoz
 clean             átmeneti állománzok törlése
 commands          ez a lista angolul :)
 daily-upgrade     egy update madj egy dist-upgrade végrehajtása
 dependents        a megadott csomagtól függő csomagok listája
 describe          egysoros csomag információ
 describe-new      egysoros csomag információ az új csomagokhoz
 detail            teljes leírás a csomagról
 detail-new        teljes leírás az új csomagról
 dist-upgrade      disztribúció frissítés
 docs              segítség
 download          csak letölti a telepíthető csomagot
 file-download     szövegálomanyban felsorolt csomagokat mind letölti
 file-install      szövegálomanyban felsorolt csomagokat telepít
 file-remove       szövegálomanyban felsorolt csomagokat eltávolít
 find-file         telepített csomagokban állomány keresés
 find-pkg          apt-get.org-on keres nem hivatalos csomagra
 fix-configure     egyenértékű: dpkg --configure -a (tehát újra konfigurál egy csomagot)
 fix-install       végrehajt egy: apt-get -f install (javítja a hibásan telepített függőségeket)
 fix-missing       végrehajt egy: apt-get --fix-missing upgrade
 force             csomag teleítéskor figyelmen kívül hagy felülírási és függőségi figyelmeztetéseket
 help              dokumentáció (részletesség függ a --verbose kapcsolótól)
 hold              a felsorolt csomagokat "megtart" állapotba teszi, így azok kimaradnak a frissítésekből
 init              JIG arhív állományok inicializálása
 install           csoamag(ok) telepítése (vagy frissítése) hálózatról vagy lokális .deb állomány telepítése
 installr          csoamag(ok) telepítése ajánlott csomagokkal együtt
 installrs         csoamag(ok) telepítése ajánlott és javasolt csomagokkal együtt
 installs          csoamag(ok) telepítése javasolt csomagokkal együtt
 install/dist      csoamag(ok) telepítése megadott distribúcióból
 integrity         telepített csomagok integritás ellenőrzése (checksummal)
 large          feltelepített nagy méretű csomagok listája (>10MB)
 last-update    utolsó frissítés időpontjának lekérdezése
 list           telepített csomagok listája státusszal
 list-all       csomaglista, csomagonként egy soros
 list-alts      ojektumok listája amlyekhez lehet alternatív csomagokat definiálni
 list-cache     letöltési átmeneti tároló listája
 list-commands  segítség, minden utasításról egy sor
 list-daemons   dámonok listája amelyeket lehet kezelni a JIGgel
 list-files     a megadott csomag állományainak listája
 list-hold      megtartott(hold) csomagok listája
 list-installed telepített csomagok listája, szűkíthető
 list-log       install log tartalma
 list-names     a teljes ismert csomagok lista, szűkíthető
 list-orphans   elárvult csomagok listája
 list-section   szekcióhoz tartozó csomagok listája, paraméter nélkül a szekciók listája
 list-status    hasonló mint a list, de csak az első két oszlopot listázza, teljes
 list-wide      hasonló mint a list, de ez igazán teljes
 local-dist-upgrade disztribúció frissítés már előre letöltött csomagokból
 local-upgrade  frissítés már előre letöltött csomagokból
 move           a letöltési átmeneti tár tartalmát lokális tükörbe mozgatja
 new            újonnan hozzáférhető csomagok listája
 news           híreket ad a megadott csomagról
 new-upgrades   új fissítendő csomagok listája
 non-free       telepített nem ingyenes csomagok listája
 orphans        olyan összetevők listája amiket egyetlen csomag sem használ. aka feleslegesek
 package        telepített csomagból deb csomag visszanyerése
 policy         elsőbbségek szabályok listája ha hozzáférhető
 purge          teljes eltávolítás még a konfigurációs állományokat is!
 purge-depend   teljes eltávolítás függőségekkel együtt
 purge-orphans  felesleges csomagok teljes eltávolítása
 readme         dokumentáció kilistázása a /usr/share/doc-ból
 recursive      csomagok letöltése függőségekkel együtt
 recommended    csomag telepítése az hozzá ajánlott csomagokkal együtt
 reconfigure    csomag beállítása újra gkconfiggal
 reinstall      csomag(ok) újratelepítése
 reload         démon konfigurációs állományának újratöltése
 remove        csomag(ok) eltávolítása
 remove-depend  csomag és függőségeinek eltávolítása
 remove-orphans elárvult csomagok eltávolítása
 repackage      telepített csomagból deb csomag visszanyerése
 reset          JIG archív inicializálása
 restart        démon újraindítása
 rpm2deb        RedHat .rpm állomány konvertálás Debian .deb állománnyá
 rpminstall     RedHat .rpm csmag telepítése
 rpmtodeb       azonos mint rpm2deb
 search       csomag keresése kulcsszóval
 search-apt     lokális Debian archív keresése sources.list számára
 setup          sources.list konfigurálása menüvel támogatva
 show           csomag részletes infomrációja
 showdistupgrade disztribúció frissítés szimulálása
 showinstall    telepítés szimulálása
 showremove     csomag eltávolítás szimulálása
 showupgrade    frissítés szimulálása
 size           telepített vagy megadott csomag méretének listázása kbyte-ban
 sizes          azonos az előzővel
 snapshot       egy lista generálása telepített csomaggal és verzióval benne
 source         letölti a megadott csomag forrását
 start          démon indítás
 status       verzió és státusz listázása a megadott csomaghoz
 status-match   a telepített és telepíthető csomagok összevetése
 status-search  telepített és hozzáférhető csomag keresése
 stop           démon megállítása
 suggested      csomag telepítése a hozzá ajánlott csomagokkal együtt
 tasksel        Gnome csomag csoport telepítő indítása
 toupgrade      frissítendő csomagok listája
 unhold         megtartás levétele a megadott csomagról
 unofficial     csomag keresése az apt-get.org-on
 update         hozzáférhető csomagok listájának frissítése
 update-alts    alternatívák frissítése
 upgrade        frissítés
 whatis         azonos a describe utasítással
 whichpkg       utasítás, állomány keresése csomagokban

Parancssori opciók:

 -h|--help      dokumentáció kiírása.
 -q|--quiet     csendes üzemmód.
 -s|--simulate  telepítési folyamat szimulálása, ellenőrzése.
 -t|--teaching  tanító mód, kiírja a végrehajtáshoz szükséges parancsokat.
 -v|--verbose=n beszédesség szintjének beállítása.
```

A teljes dokumentáció megtalálható a [togaware.com](http://www.togaware.com/wajig)-on.
