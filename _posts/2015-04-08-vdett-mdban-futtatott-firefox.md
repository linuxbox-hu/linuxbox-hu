---
excerpt: "Régóta szerettem volna valamit amivel kicsit biztonságosabbnak érezhetem
  a bankolást, annál mintha a mindenféle kiterjesztéssel telepakolt Firefoxot használnám
  amivel egyébként minden mást is böngészek a világhálón.\r\n\r\nValahogy a <a href=\"https://www.qubes-os.org/\"
  target=\"blank\">Qubes OS</a>, bár az elgondolás nem rossz, a túl sok erőforrás
  igény és nehézkes kezelés miatt sose volt igazán vonzó.\r\n\r\nAztán jött a <a href=\"https://www.docker.com/\"
  target=\"blank\">Docker</a> láz, és volt mindenféle <a href=\"https://registry.hub.docker.com/search?q=firefox&searchfield=\"
  target=\"blank\">firefox konténer</a> ami közül lehet választani. Nekem a <a href=\"https://registry.hub.docker.com/u/chrisdaish/firefox/\"
  target=\"blank\">chrisdaish</a> féle tetszett meg, Ubuntu alapokon. Úgyhogy az Ő
  munkáját vettem alapul az ötlet megvalósításához.\r\n"
categories:
- firefox
layout: story
author: szimszon
title: Védett módban futtatott Firefox
created: 1428519872
---
Régóta szerettem volna valamit amivel kicsit biztonságosabbnak érezhetem a bankolást, annál mintha a mindenféle kiterjesztéssel telepakolt Firefoxot használnám amivel egyébként minden mást is böngészek a világhálón.

Valahogy a <a href="https://www.qubes-os.org/" target="blank">Qubes OS</a>, bár az elgondolás nem rossz, a túl sok erőforrás igény és nehézkes kezelés miatt sose volt igazán vonzó.

Aztán jött a <a href="https://www.docker.com/" target="blank">Docker</a> láz, és volt mindenféle <a href="https://registry.hub.docker.com/search?q=firefox&searchfield=" target="blank">firefox konténer</a> ami közül lehet választani. Nekem a <a href="https://registry.hub.docker.com/u/chrisdaish/firefox/" target="blank">chrisdaish</a> féle tetszett meg, Ubuntu alapokon. Úgyhogy az Ő munkáját vettem alapul az ötlet megvalósításához.
<!--break-->
Miről is van szó? A <a href="https://www.docker.com/" target="blank">Docker</a> a Linux kernel névtereit használja, és ezáltal képes elszeparálni a processzeket egymástól. Külön fájlrendszert lát a konténerben futtatott program, ami ráadásul minden indításnál eredeti állapotába kerül. Tehát nincs history, nincs semmi mentett változás. Hálózat szintjén is virtuális hálózatra kerül a futó kód stb. A <a href="https://www.docker.com/" target="blank">Docker</a>ről bővebben <a href="http://docs.docker.com/" target="blank">itt</a>. Ráadásul a <a href="https://www.docker.com/" target="blank">Docker</a> olyan technológia ami kimondottan egy-egy program futtatására való. Éppen ez kell nekem. Egy tiszta Firefox telepítés - már amennyire lehet, mert a Java és Flash bele van telepítve -, minden járulékos sallangtól mentes, nincs add-on, nincs semmi. Viszont azt érdemes észben tartani, hogy a <a href="https://www.docker.com/" target="blank">Docker</a> jelen esetben egy minimális Ubuntu rendszert használ kiindulási alapnak és ide szabványos úton telepíti (apt-get) a Java-t, Flash-t és Firefox-ot, annak minden szükséges függőségével együtt! Így az elkészül képfájl összességében több száz MB is lehet. Viszont ha egy képfájl része egy másiknak akkor az nem fog elfoglalni újabb helyet, egyszerűen újra lesz hasznosítva.

De mi is kell hozzá?

 <a href="https://www.docker.com/" target="blank">Docker</a> telepítés Ubuntu-n (további telepítési útmutató <a href="http://docs.docker.com/installation/" target="blank">itt</a>):
<code>
$ wget -qO- https://get.docker.com/ | sh
</code>
Itt érdemes a felhasználónkat bevenni a docker csoportba:
<code>
$ sudo adduser ...felhasználónk... docker
</code>
Itt érdemes kijelentkezni és vissza, hogy a felhasználónk ténylegesen rendelkezzen a docker csoport tagsággal.
 
Ezzel a <a href="https://www.docker.com/" target="blank">Docker</a> felkerült a gépre és el lehet kezdeni használni az image-et. Ehhez érdemes letölteni az indító fájlt:
<code>
$ wget "https://raw.githubusercontent.com/szimszon/firefox-docker/master/firefox-docker.sh"
</code>
Érdemes körülnézni a script első részében, ahol a változók vannak és beállítani amit kell:
<code>
# Docker image neve - nem kell bántani, hacsak nem lesz frissítés :)
DOCKER_IMAGE="szimszon/firefox:v2"
# Running Docker konténer neve - nem kell bántani
DOCKER_NAME="firefox-docker"
# PulseAudio szerver címe (ifconfig docker0 -- parancsot kiadva megtudhatjuk az IP címet)
PULSE_SERVER="172.17.42.1:4713"
# A felhasználónk Letöltések könyvtára - alapból az angol megfelelő van beírva! 
ORIGINAL_DOWNLOADS="$HOME/Letöltések/$DOCKER_NAME"
</code>
Ha megszerkesztettük, mentsük el és el is indíthatjuk:
<code>
$ chmod +x firefox-docker.sh
$ ./firefox-docker.sh
</code>
Ha minden jól megy, akkor kis idő múlva letöltődik az image, létrejön a konténer és elindul benne  a Firefox böngésző, ami megjelenik a grafikus felületen. Amikor a Firefox-ból kilépünk a konténer meg is szűnik, de a letöltött lemezkép nem. Újbóli elindításnál már nem fogja letölteni, de az image-ből új konténer jön létre és tiszta lappal indul a böngésző.

Ahhoz, hogy hangunk is legyen, be kell állítani a PulseAudio szervert, hogy hálózaton azonosítás nélkül lehessen hozzá csatlakozni. Ehhez a paprefs csomagra lesz szükség, ha nincs fenn telepítsük:
<code>
$ sudo apt-get install paprefs
$ paprefs
</code>
A <strong>Network server</strong> fülön állítsuk be <strong>Hálózati hozzáférés engedélyezése a helyi hangeszközökhöz</strong> opciót és ezen belül a <strong>Don't requires authentication</strong>-ot. Ez után a legjobb, ha újraindítjuk a számítógépet, de lehet, hogy elég a ki-,és bejelentkezés.

Ha ezek után indítjuk el a firefox-docker.sh-t és jól adtuk meg az IP-t és portszámot a PulseAudio-hoz a hangnak is működnie kell.

Ha szeretnénk az Unity oldalsávján lévő Firefox ikonon jobb egérgombbal egy menüből indítani akkor másoljuk le a rendszer firefox.desktop fájlját a Saját könyvtárunkba:
<code>
$ cp /usr/share/applications/firefox.desktop $HOME/.local/share/applications/firefox.desktop
</code>
És keressük meg a <strong>[Desktop Entry]</strong> részben a <strong>Actions=NewWindow;NewPrivateWindow</strong> sort és írjuk a végére, hogy <i>;DockerFirefox</i>:
<code>
Actions=NewWindow;NewPrivateWindow;DockerFirefox
</code>
Majd a fájl végére illesszük be az alábbi részt:
<code>
[Desktop Action DockerFirefox]
Name=Docker Firefox
Exec=/...teljes elérési út.../firefox-docker.sh
OnlyShowIn=Unity;
</code>
A ki-, és bejelentkezés után az Indítóban a Firefox ikonra jobb egérgombbal kattintva egy új menün keresztül kattintással indítható a konténerbe zárt Firefox.

Ha valaki nem bízik a <a href="https://registry.hub.docker.com/" target="blank">Docker Hub</a> által generált lemezképben, nem kell mást tennie, mit letölteni a Docker definíciós fájlt is tartalmazó Git tárólót és elkészíteni a saját lemezképet:
<code>
$ wget -Ofirefox-docker.zip "https://github.com/szimszon/firefox-docker/archive/master.zip"
$ unzip firefox-docker.zip
$ cd firefox-docker-master
$ docker build -t szimszon/firefox-docker --no-cache .
</code>
és máris használható a saját készítésű Firefox image.

Kellemes böngészést!

Projekt a Docker Hub-on: <a href="https://registry.hub.docker.com/u/szimszon/firefox-docker/" target="blank">itt</a>
Projekt a GitHUB-on: <a href="https://github.com/szimszon/firefox-docker" target="blank">itt</a>
