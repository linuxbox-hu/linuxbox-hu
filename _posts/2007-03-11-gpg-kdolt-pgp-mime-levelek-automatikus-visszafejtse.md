---
excerpt: "<h1><a title=\"http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2\"
  target=\"_blank\" href=\"http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2\">mail_gpg_extract.py</a><a
  title=\"http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2.asc\"
  target=\"_blank\" href=\"http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2.asc\">.asc</a>\r\n
  \ <br />\r\n</h1>\r\n<p>Ez egy olyan script, ami automatikusan kicsomagolja a megfelelő
  <i>gpg/pgp</i> kulccsal titkosított és aláírt leveleket.\r\n  <br />\r\n  "
categories:
- linux
layout: story
author: szimszon
title: GPG kódolt (pgp-mime) levelek automatikus visszafejtése
created: 1173630397
---
<h1><a title="http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2" target="_blank" href="http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2">mail_gpg_extract.py</a><a title="http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2.asc" target="_blank" href="http://linux.oregpreshaz.eu/cucc/mail_gpg_extract/mail_gpg_extract.tar.bz2.asc">.asc</a>
  <br />
</h1>
<p>Ez egy olyan script, ami automatikusan kicsomagolja a megfelelő <i>gpg/pgp</i> kulccsal titkosított és aláírt leveleket.
  <br />
  <br /> Felhasználható például olyan esetekben, amikor egy szervernek hiteles forrásból érkező utasítást/szöveget/fájlt szeretnénk levél útján eljuttatni.
  <br />
  <br />A script önmagában a következőt teszi:
  <br />
</p>
<ul>
  <li>az alapértelmezett bemenetről érkező levelet fogadja és ,,pgp-encrypted'' Content-type-ot keres benn.</li>
  <li>ha nem talál, akkor a levelet (egy naplóbejegyzés után) eldobja</li>
  <li>a gpg titkosított és aláírt levelet visszafejti és</li>
  <li>egy a parancssorban megadott könyvtárba kitömöríti
  <br /></li>
  <li>így tetszőleges program elvégezheti a további műveleteket
  <br /></li>
</ul>
<p>
  <br />A könyvtár struktúrája ahova a visszafejtett levél el lesz mentve:
  <br />
</p>
<ul>
  <li> minden levél külön könyvtárba kerül, ennek a könyvtárnak a neve a levél érkezésének időbéllyege (time.time())</li>
  <li>a levélhez tartozó könyvtárba a könyvtár nevével megegyező időbélyeg nevű fájlba belekerül a:</li>
  <li>
  <pre>------- cut -------
From: &lt;az eredeti levél feladója&gt;
Subject: &lt;az eredeti levél tárgya&gt;</pre>
  <pre>&lt;a gpg program kimenete - milyen kulccsal titkosították és írták alá a levelet&gt;
------- cut -------</pre></li>
</ul>
<ul>
  <li> a könyvtár további tartalma a visszafejtett levél tartalma és fájljai</li>
</ul>
<p><i>A program nem végez semmiféle rekurzív levél kibontást vagy fájl kitömörítést!</i>
  <br />
  <br />
</p>
<h2>Előfeltételek
</h2>
<p>A program <i>Python2.4</i>-gyel lett tesztelve és az alábbi modulokat használja:
  <br />
</p>
<ul>
  <li>email</li>
  <li>mimetypes</li>
  <li>sys</li>
  <li>os</li>
  <li>GnuPGInterface</li>
  <li>re</li>
  <li>time</li>
  <li>getopt</li>
  <li>tempfile</li>
  <li>segito
  <br /></li>
</ul>
<p>
  <br />
</p>
<h2>Telepítés
</h2>
<p>Másoljuk a <i>mail_gpg_extract.py</i> scriptet és <i>segito.py</i> modult bárhova egy közös könyvtárba.
  <br />
  <br />
</p>
<h2>Program használata
</h2>
<pre>&lt;mail az alapért.bemenetrol&gt; | mail_exec.py -d &lt;könyvtár&gt; [-p &lt;jelmondat&gt;]</pre>
<p><b>könyvtár </b> - a könyvtár ahova a visszafejtett levelek mentésre kerülnek
  <br /><b>jelmondat </b>- gpg/pgp kulcshoz tartozó jelmondat
  <br />
  <br />A jelmondatot három féle képpen lehet megadni:
  <br />
</p>
<ul>
  <li>a programban: <font face="courier new,courier,monospace">parameters.set_passphrase('&lt;jelmondat&gt;')</font></li>
  <li>paraméterrel: -p &lt;jelmondat&gt;</li>
  <li>környezeti válozóban: <font face="courier new,courier,monospace">export PASSPHRASE="&lt;jelmondat&gt;"</font>
  <br /></li>
</ul>
<p>
  <br />
</p>
<h2>Példa .procmailrc
</h2>
<p>
</p>
<pre>-------------- cut ----------------
MAIL_GPG_EXTRACT="/home/robot/bin/mail_gpg_extract.py"
QUEUE_GPGMAIL="/home/robot/.queue_gpgmail"
:0
* ^To.*gpgmail
| ${MAIL_GPG_EXTRACT} -d ${QUEUE_GPGMAIL}
-------------- cut ----------------</pre>
<ul>
  <li>A példa működéséhez létre kell hozni egy ,,robot'' nevű felhasználót, akinek a jogaival fog futni a ,,mail_gpg_extract.py'' script.</li>
  <li>A robot saját könyvtárán belül a ,,bin'' könyvtárba másoljuk a scriptet és a segito.py modult.</li>
  <li>Továbbá szükség van a robot felhasználó által beállítani a gnupg/pgp programokat, és a kulcs cserét ugyanúgy megtenni, mintha elő személlyel szeretnénk gpg/pgp-vel kódoltan és aláírtan levelezni.</li>
  <li>Célszerű ha a ,,robot'' felhasználó csak azokat a gpg/pgp kulcsokat ismeri akiktől elfogadhat levelet.
  <br /></li>
</ul>
<h2>Garancia
</h2>
<p>A programmal kapcsolatban nem vállalok semmiféle garanciát. Bízom benne, hogy a script azt csinálja és csak azt amire megírtam :)
  <br />
  <br />
</p>
<h2>Licenc
</h2>
<p>GPLv2
  <br />
  <br />
</p>
<h2>Végszó
</h2>
<p>Nem hiszem, hogy a script aktívan fejlesztve lesz, minden hibajavítást,
  <br />észrevételt szívesen veszek!
  <br />
  <br /><i>Mindenkinek jó munkát!</i>
  <br />
</p> 
