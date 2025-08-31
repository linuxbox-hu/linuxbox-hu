---
excerpt: "<p><font face=\"Verdana\" size=\"6\">KeePass Password Safe</font>\r\n  <br
  />\r\n</p>\r\n<p><a title=\"http://keepass.info/\" target=\"_blank\" href=\"http://keepass.info/\">http://keepass.info/\r\n
  \ <br /></a>\r\n</p>\r\n<p>Kell egy olyan program ami intelligensen kezeli a millió
  egy jelszót? A jelszavakat titkosítva tárolja és átjárható az operációs rendszerek
  között beleértve az Androidot is?\r\n</p>\r\n<p>&nbsp;Tegnap este akadtam rá a KeePass
  2.x-es változatára ami megfelelőnek tűnik.\r\n</p>\r\n"
categories:
- hírek
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: KeePass2 a jelszótároló mindenes
created: 1365449012
---
<p><font face="Verdana" size="6">KeePass Password Safe</font>
  <br />
</p>
<p><a title="http://keepass.info/" target="_blank" href="http://keepass.info/">http://keepass.info/
  <br /></a>
</p>
<p>Kell egy olyan program ami intelligensen kezeli a millió egy jelszót? A jelszavakat titkosítva tárolja és átjárható az operációs rendszerek között beleértve az Androidot is?
</p>
<p>&nbsp;Tegnap este akadtam rá a KeePass 2.x-es változatára ami megfelelőnek tűnik.
</p>
<!--break-->
<ul>
  <li>AES, Rijndael (SHA-256 hash) titkosítás használata a jelszavak tárolására</li>
  <li>Az adatbázis jelszóval és/vagy kulcsfájllal is védhető</li>
  <li>Létezik Win98 / WinME / Win2000 / Win XP... verzió (.Net keretrendszer kell hozzá), Linux, BSD (Mono keretrendszer kell hozzá), Mac OS X, PocketPC, Smartphone. Letöltés <a title="Letölés oldal" target="_blank" href="http://keepass.info/download.html">itt</a>.</li>
  <li>Exportálás TXT, HTML, XML, CSV struktúrába</li>
  <li>Importálás Password Keeper-ből, Password Agent-ből, CodeWalletPro, Password Safe v2 <a title="Help: Import" target="_blank" href="http://keepass.info/help/base/importexport.html">stb...</a></li>
  <li>Az egész adatbázis egy fájl</li>
  <li>Fájl csatolmányok adhatók a bejegyzésekhez</li>
  <li>Auto-type, az ablak címe alapján kikeresi a megfelelő bejegyzést és automatikusan beírja (képes arra, hogy az egyik felét a jelszónak billentyűzet emulációval a másik felét vágólapról betenni - így nehezítve a dolgát a keyloggereknek vagy vágólap figyelőknek)</li>
  <li>Csoportok, [al[-al[...]]]csoportok kezelése</li>
  <li>Több adatbázis együttes használata</li>
  <li>Kiterjesztésekkel bővíthető funkcionalitás (Figyelem van ami csak Windows only :( )</li>
  <li>Nyílt forráskód. KeePass is OSI Certified Open Source Software. OSI Certified is a certification mark of the Open Source Initiative.</li>
</ul>
<p>Letöltések <a title="Letölés oldal" target="_blank" href="http://keepass.info/download.html">itt</a>.
</p>
<p>Még egy érdekes bővitményre hívnám fel a figyelmet a <a title="Figyelem, vannak Windows ONLY kiterjesztések" target="_blank" href="http://keepass.info/plugins.html">rengeteg másik</a> mellett. Ez az <a title="KeeFox" target="_blank" href="http://keefox.org/">KeeFox</a>, melynek használatával a Firefox beépített jelszókezelőjét tudjuk kiváltani úgy, hogy a jelszavak nem a böngészőbe kerül elmentésre, hanem a KeePass v2 adatbázisába, amit egy RPC hívással képes elérni. Linux alatt Ubuntut használva a KeePass plugin könyvtára: /usr/lib/keepass2/plugins. Azon kívül ajánlatos telepíteni a teljes Mono keretrendszert (mono-complete), különben a KeeFox bővitmény nem fog működni.
</p>
<p>Aki nem akar a KeeFox-szal bajlódni annak még mindig ott van az Auto-type, amihez Linux alatt az <a title="van csomagban Ubuntu alatt" target="_blank" href="https://github.com/jordansissel/xdotool">xdotool</a> csomag szüksége ami X alatt képes billentyűzetet és egeret emulálni. Unity alatt <em>Rendszerbeállítások -&gt; Billentyűzet -&gt; Gyorsbillentyűk -&gt; Egyedi...</em> Név: <strong>KeePass Auto-Type</strong>, Parancs: <strong>/usr/bin/keepass2 --auto-type</strong> majd adjunk hozzá egy kívánt billentyű kombinációt, pl.: &lt;<em>CTRL&gt;+&lt;ALT&gt;+A</em>
</p>
<p><em></em>Kellemes ismerkedést a programmal.
  <br />
</p>
<ul>
</ul>
