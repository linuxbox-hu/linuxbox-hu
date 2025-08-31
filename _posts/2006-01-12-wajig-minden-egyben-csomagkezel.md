---
excerpt: "Wajig mindenféle műveletre képes ami szóba kerülhet csomagokkal, démonokkal
  kapcsolatban.\r\nÍme a teljes JIG utasítás készlet:\r\n\r\n <strong>addcdrom</strong>
  \         CD-ROM hozzáadás a csomagok forrásaihoz\r\n <strong>auto-alts</strong>
  \        alternatív csomag megmutatása (prioritások használatával)\r\n <strong>auto-clean</strong>
  \       etöltött és telepített csomagok törlése az átmenti tárból\r\n <strong>auto-download</strong>
  \    frissülő csomagok letöltése majd telepítése\r\n <strong>auto-install</strong>
  \     telepítés interaktivitás nélkül\r\n <strong>available</strong>         hozzáférhető
  és telepíthető összes csomag listája\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: wajig - minden egyben csomagkezelő
created: 1137058446
---
Wajig mindenféle műveletre képes ami szóba kerülhet csomagokkal, démonokkal kapcsolatban.
Íme a teljes JIG utasítás készlet:

 <strong>addcdrom</strong>          CD-ROM hozzáadás a csomagok forrásaihoz
 <strong>auto-alts</strong>         alternatív csomag megmutatása (prioritások használatával)
 <strong>auto-clean</strong>        etöltött és telepített csomagok törlése az átmenti tárból
 <strong>auto-download</strong>     frissülő csomagok letöltése majd telepítése
 <strong>auto-install</strong>      telepítés interaktivitás nélkül
 <strong>available</strong>         hozzáférhető és telepíthető összes csomag listája
 <strong>bug</strong>               jelentett hibák ellenőrzése a Debian hibajelentő rendszerben
 <strong>build</strong>             letölti a forrás csomagot és deban csomagot készít
 <strong>build-depend</strong>      letölti a megadott csomag függőségeit forrásból és elkészíti a csomagokat
 <strong>changelog</strong>         letölti az legutolsó változások listáját a csomaghoz
 <strong>clean</strong>             átmeneti állománzok törlése
 <strong>commands</strong>          ez a lista angolul :)
 <strong>daily-upgrade</strong>     egy update madj egy dist-upgrade végrehajtása
 <strong>dependents</strong>        a megadott csomagtól függő csomagok listája
 <strong>describe</strong>          egysoros csomag információ
 <strong>describe-new</strong>      egysoros csomag információ az új csomagokhoz
 <strong>detail</strong>            teljes leírás a csomagról
 <strong>detail-new</strong>        teljes leírás az új csomagról
 <strong>dist-upgrade</strong>      disztribúció frissítés
 <strong>docs</strong>              segítség
 <strong>download</strong>          csak letölti a telepíthető csomagot
 <strong>file-download</strong>     szövegálomanyban felsorolt csomagokat mind letölti
 <strong>file-install</strong>      szövegálomanyban felsorolt csomagokat telepít
 <strong>file-remove</strong>       szövegálomanyban felsorolt csomagokat eltávolít
 <strong>find-file</strong>         telepített csomagokban állomány keresés
 <strong>find-pkg</strong>          apt-get.org-on keres nem hivatalos csomagra
 <strong>fix-configure</strong>     egyenértékű: dpkg --configure -a (tehát újra konfigurál egy csomagot)
 <strong>fix-install</strong>       végrehajt egy: apt-get -f install (javítja a hibásan telepített függőségeket)
 <strong>fix-missing</strong>       végrehajt egy: apt-get --fix-missing upgrade
 <strong>force</strong>             csomag teleítéskor figyelmen kívül hagy felülírási és függőségi figyelmeztetéseket
 <strong>help</strong>              dokumentáció (részletesség függ a --verbose kapcsolótól)
 <strong>hold</strong>              a felsorolt csomagokat "megtart" állapotba teszi, így azok kimaradnak a frissítésekből
 <strong>init</strong>              JIG arhív állományok inicializálása
 <strong>install</strong>           csoamag(ok) telepítése (vagy frissítése) hálózatról vagy lokális .deb állomány telepítése
 <strong>installr</strong>          csoamag(ok) telepítése ajánlott csomagokkal együtt
 <strong>installrs</strong>         csoamag(ok) telepítése ajánlott és javasolt csomagokkal együtt
 <strong>installs</strong>          csoamag(ok) telepítése javasolt csomagokkal együtt
 <strong>install/dist</strong>      csoamag(ok) telepítése megadott distribúcióból
 <strong>integrity</strong>         telepített csomagok integritás ellenőrzése (checksummal)
 <strong>large</strong>          feltelepített nagy méretű csomagok listája (>10MB)
 <strong>last-update</strong>    utolsó frissítés időpontjának lekérdezése
 <strong>list</strong>           telepített csomagok listája státusszal
 <strong>list-all</strong>       csomaglista, csomagonként egy soros
 <strong>list-alts</strong>      ojektumok listája amlyekhez lehet alternatív csomagokat definiálni
 <strong>list-cache</strong>     letöltési átmeneti tároló listája
 <strong>list-commands</strong>  segítség, minden utasításról egy sor
 <strong>list-daemons</strong>   dámonok listája amelyeket lehet kezelni a JIGgel
 <strong>list-files</strong>     a megadott csomag állományainak listája
 <strong>list-hold</strong>      megtartott(hold) csomagok listája
 <strong>list-installed</strong> telepített csomagok listája, szűkíthető
 <strong>list-log</strong>       install log tartalma
 <strong>list-names</strong>     a teljes ismert csomagok lista, szűkíthető
 <strong>list-orphans</strong>   elárvult csomagok listája
 <strong>list-section</strong>   szekcióhoz tartozó csomagok listája, paraméter nélkül a szekciók listája
 <strong>list-status</strong>    hasonló mint a list, de csak az első két oszlopot listázza, teljes
 <strong>list-wide</strong>      hasonló mint a list, de ez igazán teljes
 <strong>local-dist-upgrade</strong> disztribúció frissítés már előre letöltött csomagokból
 <strong>local-upgrade</strong>  frissítés már előre letöltött csomagokból
 <strong>move</strong>           a letöltési átmeneti tár tartalmát lokális tükörbe mozgatja
 <strong>new</strong>            újonnan hozzáférhető csomagok listája
 <strong>news</strong>           híreket ad a megadott csomagról 
 <strong>new-upgrades</strong>   új fissítendő csomagok listája
 <strong>non-free</strong>       telepített nem ingyenes csomagok listája
 <strong>orphans</strong>        olyan összetevők listája amiket egyetlen csomag sem használ. aka feleslegesek
 <strong>package</strong>        telepített csomagból deb csomag visszanyerése
 <strong>policy</strong>         elsőbbségek szabályok listája ha hozzáférhető
 <strong>purge</strong>          teljes eltávolítás még a konfigurációs állományokat is!
 <strong>purge-depend</strong>   teljes eltávolítás függőségekkel együtt
 <strong>purge-orphans</strong>  felesleges csomagok teljes eltávolítása
 <strong>readme</strong>         dokumentáció kilistázása a /usr/share/doc-ból
 <strong>recursive</strong>      csomagok letöltése függőségekkel együtt
 <strong>recommended</strong>    csomag telepítése az hozzá ajánlott csomagokkal együtt
 <strong>reconfigure</strong>    csomag beállítása újra gkconfiggal
 <strong>reinstall</strong>      csomag(ok) újratelepítése
 <strong>reload</strong>         démon konfigurációs állományának újratöltése
 <strong>remove</strong>        csomag(ok) eltávolítása
 <strong>remove-depend</strong>  csomag és függőségeinek eltávolítása
 <strong>remove-orphans</strong> elárvult csomagok eltávolítása
 <strong>repackage</strong>      telepített csomagból deb csomag visszanyerése
 <strong>reset</strong>          JIG archív inicializálása
 <strong>restart</strong>        démon újraindítása
 <strong>rpm2deb</strong>        RedHat .rpm állomány konvertálás Debian .deb állománnyá
 <strong>rpminstall</strong>     RedHat .rpm csmag telepítése
 <strong>rpmtodeb</strong>       azonos mint rpm2deb
 <strong>search</strong>       csomag keresése kulcsszóval
 <strong>search-apt</strong>     lokális Debian archív keresése sources.list számára
 <strong>setup</strong>          sources.list konfigurálása menüvel támogatva
 <strong>show</strong>           csomag részletes infomrációja
 <strong>showdistupgrade</strong> disztribúció frissítés szimulálása
 <strong>showinstall</strong>    telepítés szimulálása
 <strong>showremove</strong>     csomag eltávolítás szimulálása
 <strong>showupgrade</strong>    frissítés szimulálása
 <strong>size</strong>           telepített vagy megadott csomag méretének listázása kbyte-ban
 <strong>sizes</strong>          azonos az előzővel
 <strong>snapshot</strong>       egy lista generálása telepített csomaggal és verzióval benne
 <strong>source</strong>         letölti a megadott csomag forrását 
 <strong>start</strong>          démon indítás
 <strong>status</strong>       verzió és státusz listázása a megadott csomaghoz
 <strong>status-match</strong>   a telepített és telepíthető csomagok összevetése
 <strong>status-search</strong>  telepített és hozzáférhető csomag keresése
 <strong>stop</strong>           démon megállítása
 <strong>suggested</strong>      csomag telepítése a hozzá ajánlott csomagokkal együtt
 <strong>tasksel</strong>        Gnome csomag csoport telepítő indítása
 <strong>toupgrade</strong>      frissítendő csomagok listája
 <strong>unhold</strong>         megtartás levétele a megadott csomagról
 <strong>unofficial</strong>     csomag keresése az apt-get.org-on
 <strong>update</strong>         hozzáférhető csomagok listájának frissítése
 <strong>update-alts</strong>    alternatívák frissítése
 <strong>upgrade</strong>        frissítés
 <strong>whatis</strong>         azonos a describe utasítással
 <strong>whichpkg</strong>       utasítás, állomány keresése csomagokban

Parancssori opciók:

 -h|--help      dokumentáció kiírása.
 -q|--quiet     csendes üzemmód.
 -s|--simulate  telepítési folyamat szimulálása, ellenőrzése.
 -t|--teaching  tanító mód, kiírja a végrehajtáshoz szükséges parancsokat.
 -v|--verbose=n beszédesség szintjének beállítása.

A teljes dokumentáció megtalálható a <a href="http://www.togaware.com/wajig">togaware.com-on</a>.
