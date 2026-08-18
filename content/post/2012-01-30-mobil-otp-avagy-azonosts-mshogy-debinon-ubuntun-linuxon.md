---
author: szimszon
categories:
- linux
created: 1327949158
date: '2012-01-30T00:00:00Z'
description: '„So long ago... Frissítve: 2012.02.07. Készítettem egy új scriptet.'
title: Mobil-OTP avagy azonosítás máshogy Debiánon/Ubuntun/Linuxon...
aliases:
- /node/707/
- /story/707/
---
[„So long ago...](http://en.wikipedia.org/wiki/The_Hitchhiker's_Guide_to_the_Galaxy)

**Frissítve: 2012.02.07.** Készítettem egy új [scriptet](https://github.com/szimszon/motpy/)

...de kezdjük az elején. Két [Hacktion](http://tv.hir24.hu/musorinfo/sorozat/Hacktion/13394) rész között mikor felsírt a gyerek és kinn olvadt formában havazott a téli kora őszi tavaszon kinyitottam a böngészőm és azt látom, hogy kedvenc [Web2py](http://web2py.com/) web frameworkömhöz valaki készített egy [Mobil-OTP authentikációs modult](https://groups.google.com/forum/#!topic/web2py/KrCzcTGYNIQ)...

...hmm, Mobil-OTP, ez azért nem az [OTP](https://www.otpbank.hu/portal/hu/fooldal) (Országos Takarék Pénztár), mindig is szerettem volna valamit, ha vonaton utazok, vagy nyilvános helyen be kell jelentkezni valahova, a vállam fölött ne lássák már a `root` jelszót. Mondjuk azt eddig sem, mert `root`ként nem jelentkezek be sehova. Dehát vannak azért *local root exploit*ok, mint az a napokban [kiderüt](http://hup.hu/cikkek/20120123/mempodipper_linux_local_root_exploit_szabadon).

Szóval ha lenne valami, hogy olcsón, értsd 0 költséggel, hogy ne egyből a biztonsági kamera felvételén a tényleges jelszavam jelenjen meg, hanem valami ami már többször nem lesz alkalmas arra, hogy bejelentkezzen vele valaki. Na ilyen nincs. Költsége mindennek van. Ha nem anyagi akkor is a normál felhasználást bonyolító megoldásnak idő vagy egyéb vonzata akár forintosítható is. De törekedjünk a költségek csökkentésére.

Valami több elemes azonosítás kellene. Na de mi a fene az a [Mobil-One-Time-Password](http://motp.sourceforge.net/)?

Az [motp oldalán](http://motp.sourceforge.net/) ezt írják magukról:

> **Mobile One Time Passwords**
>
> **Mobile-OTP** — strong, two-factor authentication with mobile phones
>
> [Standard phone and BlackBerry (J2ME)](http://motp.sourceforge.net/#2) [iPhone](http://motp.sourceforge.net/#7) [Google Android](http://motp.sourceforge.net/#6) [Windows Phone 7](http://motp.sourceforge.net/#7) [PalmOS](http://motp.sourceforge.net/#6) [webOS](http://motp.sourceforge.net/#7) [Maemo](http://motp.sourceforge.net/#7) [Openmoko](http://motp.sourceforge.net/#7) [Universal Web App](http://motp.sourceforge.net/#6) [Windows](http://motp.sourceforge.net/#7) [Linux](http://motp.sourceforge.net/#7) [MacOS](http://motp.sourceforge.net/#7)

Hát ez jó... Legtöbbször akinek olyan gondjai vannak, hogy nehogy a válla fölött nézelődve ellopják a jelszavát ilyen kemény téli időjárásban, ahol még a Mikulás szánkójáról is leolvadnak a sítalpak a kátyúkkal szabdalt [magyar aszfalt](http://www.cylex-tudakozo.hu/ceg-info/magyar-aszfalt-kft-42117.html)on. És bár nyakunkon a [szibériai fagy](http://index.hu/x.php?id=inxcl&url=http://index.hu/gazdasag/magyar/2012/01/30/zabalja_a_gazt_a_teli_hideg/) (a cikkben -11 - -12 Cfokról beszélnek, bár ugyanez az oldal egy másik [cikkében](http://index.hu/tudomany/sziberia/) így kezdi: „*Télen a hőmérő szála gyakran mínusz ötven fok alá is zuhan a közép-szibériai Tuturiban*” most akkor a rövid idejű -11 - -12 fok szibériai? Lehet onnan fúj majd a szél:) egyszóval nem bízhatunk abban sem ha csak szuszog mögöttünk valaki. És akkor nem beszéltünk még a [keylogger](http://lmgtfy.com/?q=keylogger)ekről [net-cafe](http://lmgtfy.com/?q=netcafe)kről... De vissza az eredeti témához.

Szóval tfh és itt nem a [Together For The Harvest](http://www.tfh.org.uk/)-ra gondolok, hanem tegyük fel hogy rendelkezünk legalább egy mobil telefonnal (tulajdonképpen az sem kell, van pc-s kliens is). De ha már Mobile akkor maradjunk a telefonnál.

Most akkor mi is ez?

Ez egy két faktorú beléptetést (azonosítást) megvalósító mifene. Egyrészt szükséged van valamire amit birtokolsz, esetünkben ez a telefon; és szükséged van valamire amit tudsz, ez a PIN kód. Nagyszerű. Akkor ezzel megvagyunk.

Na várjunk csak, honnan tudja a szerver, hogy melyik a telefonunk, meg PIN kódunk? Sehogy. A telefonnak nem ez a szerepe. A telefon tud valamit amit nekünk nem kell tudnunk, legalábbis nem fejből. [Esőemberek](http://www.imdb.com/title/tt0095953/) előnyben.

De akkor ez sms-be adatforgalomba kerül?

Had mondjam végig!

Szóval letöltjük a telefonra valamelyik [MOTP kliens alkalmazás](http://motp.sourceforge.net/#6)t (client-side), nekem Androidra a [DroidOTP](https://market.android.com/details?id=net.marinits.android.droidotp) jött be (csak 4 karakteres PIN-t támogat és csak MOTP-ot) több profilt is kezel. Miért is kell a több profil támogatás? Ugyanis ez a jóképességű eljárás abból áll, hogy indításnak 16 karakterből álló véletlenszerű betű és számsort kell megadni, ez az amire a telefon emlékszik majd helyettünk. 1 ilyen sorozat egy profilhoz tartozik. Ezt a karaktersorozatot a szervernek is ismernie kell. Ha megvan a karaktersorozat az eljárásnak szüksége van a pin kódra. Ezt a szervernek szintén előre ismernie kell. Majd a telefon veszi a [UNIX epoch](http://en.wikipedia.org/wiki/Unix_time)-ot másodpercben - tulajdonképpen 10-es másodperc léptékben -. a pin-t és a véletlen karaktersorozatot. Ebből a három összetevőből képez egy [md5 hash](http://en.wikipedia.org/wiki/MD5)-t és a hash első 6 karakterét megjeleníti. Ez a bejelentkezéshez használható jelszó. Szuper. Akkor nincs más hátra, mint előre. A program a telón, jó előre beélesítve, senki nem látta a véletlen karakter sorozatot, akkor mostmár jöhet a belépés bárhol.

Upsz. És a szerver? Ez már keményebb dió. Az [motp oldal](http://motp.sourceforge.net/)on több leírás is van [Radius](http://freeradius.org/)-ra és [PAM](http://en.wikipedia.org/wiki/Pluggable_authentication_module)-ra is. Most az utóbbiról beszélnék. Az is több lehetőséget kínál.

Először a [natív](http://motp.sourceforge.net/pam_mobile_otp-0.6.1.tgz) pam modult próbáltam, de ezt nem sikerült lefordítani.

Másodszor van egy [script](http://motp.sourceforge.net/PAM-script.zip) a [pam-script](http://sourceforge.net/projects/pam-script/)-hez. A libpam-script szépen telepíthető [Ubuntu](http://ubuntu.hu/)n de volt egy apró bökkenő, bizonyos esetekben a pam-script nem adta át a bejelentkezéshez az adatokat az otp scriptnek. Pl. ssh ment de a login, sudo esetében nem mentek át a paraméterek.

Nini lehet egyszerűbben is. Van egy [pam-exec](http://www.gsp.com/cgi-bin/man.cgi?section=8&topic=pam_exec) és már fenn is volt, nem kellett külön telepíteni. Csakhogy a [pam-exec](http://www.gsp.com/cgi-bin/man.cgi?section=8&topic=pam_exec) nem környezeti változóban adja át a jelszót (authtok) hanem a script alapértelmezett bemenetére.

De akkor hogy is van ez? Kezdjük a [kályhá](http://lmgtfy.com/?q=k%E1lyha)tól.

- hozzunk létre egy könyvtárat: /usr/local/otp
- és még egyet: /usr/local/otp/cache
- `chown -R root:root /usr/local/otp`
- `chmod -R go-rwx /usr/local/otp`
- kell a kicsit módosított script ([otp-auth-exec](/assets/files/posts/otp-auth-exec.txt)) -- csatolmány (a *.txt* kiterjesztést szedjétek le)
- a [pam-script](http://sourceforge.net/projects/pam-script/)-ből ki kell másolni a otp-secrets fájlt és betenni a /usr/local/otp könyvtárba. Ebben a fájlban van benn a véletlen karaktersor és pin kód a felhasználóhoz a felhasználói névhez.

Wow, ennyi volt.

Hát még nem. Még meg kell gyógyítani a [PAM](http://en.wikipedia.org/wiki/Pluggable_authentication_module)-ot. [Ubuntu](http://ubuntu.hu/)n én a következőket tettem (a módosítás `<-- ÚJ` jelöléssel):

--- sshd cut ---

```text
# PAM configuration for the Secure Shell service
auth   sufficient      pam_exec.so expose_authtok /usr/local/otp/otp-auth-exec  # <-- ÚJ
# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale
#
# Standard Un*x authentication.
#@include common-auth  # <-- ÚJ (kikommentezve)
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
```

--- sshd cut ---
Így csak MOTP-vel lehet ssh-n bejelentkezni.

--- common-auth ---

```text
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
auth   [success=3 default=ignore]      pam_exec.so expose_authtok /usr/local/otp/otp-auth-exec  # <-- ÚJ
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
```

--- common-auth ---

Így minden common-auth-ot importáló pam-ot használó alkalmazás beenged MOTP-vel vagy a rendes jelszóval.

Na álljunk csak meg egy pillanatra. Az elején arról volt szó, hogy a unix timestamp alapján generálódik a belépő kód, akkor most legjobb esetben is 10 másodpercem van belépni (10 mp-es lépték van)?

Erről szerencsére nincs szó, ha megnézzük a scriptet, látszik hogy van ±3 percünk, egyrészt az eszközök órája nem biztos, hogy pontos másrészt a 10 másodperc nem biztos, hogy elég...

Ühüm... de akkor egy-egy kód összesen 6 percig érvényes?

Nem teljesen. Csak amíg valaki be nem jelentkezik vele. Hogy valóban egy alkalmas jelszó legyen a script eltárolja a már felhasznált kódot és az legközelebb már nem lesz érvényes.

[...and thanks for all the fish”](http://en.wikipedia.org/wiki/The_Hitchhiker's_Guide_to_the_Galaxy)
