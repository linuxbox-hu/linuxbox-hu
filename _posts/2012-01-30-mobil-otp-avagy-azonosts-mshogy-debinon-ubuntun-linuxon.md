---
excerpt: "<p><a href=\"http://en.wikipedia.org/wiki/The_Hitchhiker's_Guide_to_the_Galaxy\">„So
  long ago...</a>\r\n</p>\r\n\r\n<p><strong>Frissítve: 2012.02.07.</strong>Készítettem
  egy új <a href='https://github.com/szimszon/motpy/'>scriptet</a></p>"
categories:
- linux
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: Mobil-OTP avagy azonosítás máshogy Debiánon/Ubuntun/Linuxon...
created: 1327949158
---
<p><a href="http://en.wikipedia.org/wiki/The_Hitchhiker's_Guide_to_the_Galaxy">„So long ago...</a>
</p>

<p><strong>Frissítve: 2012.02.07.</strong>Készítettem egy új <a href='https://github.com/szimszon/motpy/'>scriptet</a></p>
<p>...de kezdjük az elején. Két <a title="m1" href="http://tv.hir24.hu/musorinfo/sorozat/Hacktion/13394">Hacktion</a> rész között mikor felsírt a gyerek és kinn olvadt formában havazott a téli kora őszi tavaszon kinyitottam a böngészőm és azt látom, hogy kedvenc <a title="Web2py" href="http://web2py.com/">Web2py</a> web frameworkömhöz valaki készített egy <a href="https://groups.google.com/forum/#!topic/web2py/KrCzcTGYNIQ">Mobil-OTP authentikációs modult</a>...
</p>
<p>...hmm, Mobil-OTP, ez azért nem az <a title="OTP" href="https://www.otpbank.hu/portal/hu/fooldal">Országos Takarék Pénztár</a>, mindig is szerettem volna valamit, ha vonaton utazok, vagy nyilvános helyen be kell jelentkezni valahova, a vállam fölött ne lássák már a <em>root</em> jelszót. Mondjuk azt eddig sem, mert <em>root</em>ként nem jelentkezek be sehova. Dehát vannak azért <em>local root exploit</em>ok, mint az a napokban <a href="http://hup.hu/cikkek/20120123/mempodipper_linux_local_root_exploit_szabadon">kiderüt</a>.
</p>
<p>Szóval ha lenne valami, hogy olcsón, értsd 0 költséggel, hogy ne egyből a biztonsági kamera felvételén a tényleges jelszavam jelenjen meg, hanem valami ami már többször nem lesz alkalmas arra, hogy bejelentkezzen vele valaki. Na ilyen nincs. Költsége mindennek van. Ha nem anyagi akkor is a normál felhasználást bonyolító megoldásnak idő vagy egyéb vonzata akár forintosítható is. De törekedjünk a költségek csökkentésére.
</p>
<p>Valami több elemes azonosítás kellene. Na de mi a fene az a <a href="http://motp.sourceforge.net/">Mobil-One-Time-Password</a>?
</p>
<p><font face="arial"> </font>
</p>
<h2><font face="arial">Mobile One Time Passwords </font>
</h2><font face="arial">
<h1>Mobile-OTP
</h1><strong>strong, two-factor authentication with mobile phones</strong>
<p> <font size="-1"><a href="http://motp.sourceforge.net/#2">Standard phone and BlackBerry (J2ME)</a> <a href="http://motp.sourceforge.net/#7">iPhone</a> <a href="http://motp.sourceforge.net/#6">Google Android</a> <a href="http://motp.sourceforge.net/#7">Windows Phone 7</a> <a href="http://motp.sourceforge.net/#6">PalmOS</a> <a href="http://motp.sourceforge.net/#7">webOS</a> <a href="http://motp.sourceforge.net/#7">Maemo</a> <a href="http://motp.sourceforge.net/#7">Openmoko</a> <a href="http://motp.sourceforge.net/#6">Universal Web App</a> <a href="http://motp.sourceforge.net/#7">Windows</a> <a href="http://motp.sourceforge.net/#7">Linux</a> <a href="http://motp.sourceforge.net/#7">MacOS</a></font>
</p>
<p>Hát ez jó... Legtöbbször akinek olyan gondjai vannak, hogy nehogy a válla fölött nézelődve ellopják a jelszavát ilyen kemény téli időjárásban, ahol még a Mikulás szánkójáról is leolvadnak a sítalpak a kátyúkkal szabdalt <a href="http://www.cylex-tudakozo.hu/ceg-info/magyar-aszfalt-kft-42117.html">magyar aszfalt</a>on. És bár nyakunkon a <a href="http://index.hu/x.php?id=inxcl&amp;url=http://index.hu/gazdasag/magyar/2012/01/30/zabalja_a_gazt_a_teli_hideg/">szibériai fagy</a> (a cikkben -11 - -12 Cfokról beszélnek, bár ugyanez az oldal egy másik <a title="Tél a szibériai nomádok között" href="http://index.hu/tudomany/sziberia/">cikkében</a> így kezdi: „<em>Télen a hőmérő szála gyakran mínusz ötven fok alá is zuhan a közép-szibériai Tuturiban</em>” most akkor a rövid idejű -11 - -12 fok szibériai? Lehet onnan fúj majd a szél:) egyszóval nem bízhatunk abban sem ha csak szuszog mögöttünk valaki. És akkor nem beszéltünk még a <a href="http://lmgtfy.com/?q=keylogger">keylogger</a>ekről <a href="http://lmgtfy.com/?q=netcafe">net-cafe</a>kről... De vissza az eredeti témához.
</p>
<p> Szóval tfh és itt nem a<a href="http://www.tfh.org.uk/" class="l"> Together For The Harvest</a> -ra gondolok, hanem tegyük fel hogy rendelkezünk legalább egy mobil telefonnal (tulajdonképpen az sem kell, van pc-s kliens is). De ha már Mobile akkor maradjunk a telefonnál.
</p>
<p>Most akkor mi is ez?
</p>
<p> Ez egy két faktorú beléptetést (azonosítást) megvalósító mifene. Egyrészt szükséged van valamire amit birtokolsz, esetünkben ez a telefon; és szükséged van valamire amit tudsz, ez a PIN kód. Nagyszerű. Akkor ezzel megvagyunk.
</p>
<p> Na várjunk csak, honnan tudja a szerver, hogy melyik a telefonunk, meg PIN kódunk? Sehogy. A telefonnak nem ez a szerepe. A telefon tud valamit amit nekünk nem kell tudnunk, legalábbis nem fejből. <a href="http://www.imdb.com/title/tt0095953/">Esőemberek</a> előnyben.
</p>
<p>De akkor ez sms-be adatforgalomba kerül?
</p>
<p>Had mondjam végig!
</p>
<p>&nbsp;Szóval letöltjük a telefonra valamelyik <a title="Client-Side" href="http://motp.sourceforge.net/#6">MOTP kliens alkalmazás</a>t (client-side), nekem Androidra a <a href="https://market.android.com/details?id=net.marinits.android.droidotp">DroidOTP</a> jött be (csak 4 karakteres PIN-t támogat és csak MOTP-ot) több profilt is kezel. Miért is kell a több profil támogatás? Ugyanis ez a jóképességű eljárás abból áll, hogy indításnak 16 karakterből álló véletlenszerű betű és számsort kell megadni, ez az amire a telefon emlékszik majd helyettünk. 1 ilyen sorozat egy profilhoz tartozik. Ezt a karaktersorozatot a szervernek is ismernie kell. Ha megvan a karaktersorozat az eljárásnak szüksége van a pin kódra. Ezt a szervernek szintén előre ismernie kell. Majd a telefon veszi a <a href="http://en.wikipedia.org/wiki/Unix_time">UNIX epoch</a>-ot másodpercben - tulajdonképpen 10-es másodperc léptékben -. a pin-t és a véletlen karaktersorozatot. Ebből a három összetevőből képez egy <a href="http://en.wikipedia.org/wiki/MD5">md5 hash</a>-t és a hash első 6 karakterét megjeleníti. Ez a bejelentkezéshez használható jelszó. Szuper. Akkor nincs más hátra, mint előre. A program a telón, jó előre beélesítve, senki nem látta a véletlen karakter sorozatot, akkor mostmár jöhet a belépés bárhol.
</p>
<p>Upsz. És a szerver? Ez már keményebb dió. Az <a href="http://motp.sourceforge.net/">motp oldal</a>on több leírás is van <a href="http://freeradius.org/">Radius</a>-ra és <a href="http://en.wikipedia.org/wiki/Pluggable_authentication_module">PAM</a>-ra is. Most az utóbbiról beszélnék. Az is több lehetőséget kínál.
</p>
<p>Először a <a href="http://motp.sourceforge.net/pam_mobile_otp-0.6.1.tgz">natív</a> pam modult próbáltam, de ezt nem sikerült lefordítani.
</p>
<p>Másodszor van egy <a href="http://motp.sourceforge.net/PAM-script.zip">script</a> a <a href="http://sourceforge.net/projects/pam-script/">pam-script</a>-hez. A libpam-script szépen telepíthető <a href="http://ubuntu.hu/">Ubuntu</a>n de volt egy apró bökkenő, bizonyos esetekben a pam-script nem adta át a bejelentkezéshez az adatokat az otp scriptnek. Pl. ssh ment de a login, sudo esetében nem mentek át a paraméterek.
</p>
<p>Nini lehet egyszerűbben is. Van egy <a href="http://www.gsp.com/cgi-bin/man.cgi?section=8&amp;topic=pam_exec">pam-exec</a> és már fenn is volt, nem kellett külön telepíteni. Csakhogy a <font face="arial"><a href="http://www.gsp.com/cgi-bin/man.cgi?section=8&amp;topic=pam_exec">pam-exec</a></font> nem környezeti változóban adja át a jelszót (authtok) hanem a script alapértelmezett bemenetére.
</p>
<p>&nbsp;De akkor hogy is van ez? Kezdjük a <a href="http://lmgtfy.com/?q=k%E1lyha">kályhá</a>tól.
</p></font>
<ul>
  <li>hozzunk létre egy könyvtárat: /usr/local/otp</li>
  <li>és még egyet: /usr/local/otp/cache</li>
  <li>chown -R root:root /usr/local/otp</li>
  <li>chmod -R go-rwx /usr/local/otp</li>
  <li>kell a kicsit módosított script (<a href="http://linuxbox.hu/sites/default/files/otp-auth-exec.txt">otp-auth-exec</a>) -- csatolmány (a <em>.txt</em> kiterjesztést szedjétek le)
  <br /></li>
  <li>a <a href="http://sourceforge.net/projects/pam-script/">pam-script</a>-ből ki kell másolni a otp-secrets fájlt és betenni a /usr/local/otp könyvtárba. Ebben a fájlban van benn a véletlen karaktersor és pin kód a felhasználóhoz a felhasználói névhez.</li>
</ul>
<p>Wow, ennyi volt.
</p>
<p>Hát még nem. Még meg kell gyógyítani a <font face="arial"><a href="http://en.wikipedia.org/wiki/Pluggable_authentication_module">PAM</a></font>-ot. <a href="http://ubuntu.hu/">Ubuntu</a>n én a következőket tettem (a módosítás félkövéren):
</p>
<p>&nbsp;--- sshd cut ---
  <br />
</p>
<p><font face="courier new,courier,monospace">
# PAM configuration for the Secure Shell service
<strong>auth   sufficient      pam_exec.so expose_authtok /usr/local/otp/otp-auth-exec</strong>
# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale
#
# Standard Un*x authentication.
<strong>#@include common-auth</strong>
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional        pam_ecryptfs.so unwrap
auth    optional                        pam_cap.so 
#
# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so
#
# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so
#
# Standard Un*x authorization.
@include common-account
#
# Standard Un*x session setup and teardown.
@include common-session
#
# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]
#
# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]
#
# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so
#
# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple
#
# Standard Un*x password updating.
@include common-password

</font>--- sshd cut ---
  <br /> Így csak MOTP-vel lehet ssh-n bejelentkezni.
</p>
<p>--- common-auth ---
</p> <font face="courier new,courier,monospace">
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
# here are the per-package modules (the "Primary" block)
<strong>auth   [success=3 default=ignore]      pam_exec.so expose_authtok /usr/local/otp/otp-auth-exec</strong>
auth    [success=2 default=ignore]      pam_unix.so nullok_secure try_first_pass
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional        pam_ecryptfs.so unwrap
auth    optional                        pam_cap.so 
# end of pam-auth-update config

</font>
<p>--- common-auth ---
  <br />
</p>
<p>Így minden common-auth-ot importáló pam-ot használó alkalmazás beenged MOTP-vel vagy a rendes jelszóval.
</p>
<p>Na álljunk csak meg egy pillanatra. Az elején arról volt szó, hogy a unix timestamp alapján generálódik a belépő kód, akkor most legjobb esetben is 10 másodpercem van belépni (10 mp-es lépték van)?
</p>
<p>&nbsp;Erről szerencsére nincs szó, ha megnézzük a scriptet, látszik hogy van ±3 percünk, egyrészt az eszközök órája nem biztos, hogy pontos másrészt a 10 másodperc nem biztos, hogy elég...
</p>
<p>Ühüm... de akkor egy-egy kód összesen 6 percig érvényes?
</p>
<p>Nem teljesen. Csak amíg valaki be nem jelentkezik vele. Hogy valóban egy alkalmas jelszó legyen a script eltárolja a már felhasznált kódot és az legközelebb már nem lesz érvényes.
</p>
<p><a href="http://en.wikipedia.org/wiki/The_Hitchhiker's_Guide_to_the_Galaxy">...and thanks for all the fish”</a>
  <br />
</p>
<ul>
</ul>
