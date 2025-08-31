---
excerpt: "Ebben a bejegyzésemben egy apró de annál hasznosabb hack-et mutatok be.\r\n"
categories: []
layout: blog
author: bAndie91
mail: bandie9100@freemail.hu
title: Kalandjaim LD_PRELOAD-dal
created: 1366435307
---
Ebben a bejegyzésemben egy apró de annál hasznosabb hack-et mutatok be.
<!--break-->
Tudjuk, hogy a gyakran használt függvények és eljárások az operációs rendszer ''megosztott függvénykönyvtáraiban'' helyezkednek el és a dinamikusan linkelt programok innen idézik be saját kódjukba, ezzel lehetõséget adva, arra hogy a bináris állományuk kisebb legyen. 
Emellett az az áldásos dolog is következik ebbõl a technikából, hogy a ''shared library''-kban tárolt jól ismert függvények kiegészítésével vagy átírásával okosíthatjuk, kifigyelhetjük, eltéríthetjük a rájuk támaszkodó programokat. Preload technika, LD_PRELOAD pedig a környezeti változó neve (lásd melléklet).
Így tettem én is az [http://en.wikipedia.org/wiki/X2vnc x2vnc] program esetében.
:Az x2vnc arra való, hogy az X11 képernyõt megtoldja egy VNC által hordozott képernyõvel és továbbítsa az egérmozgást és a gépelést billentyũzetrõl. A munkaasztal megosztására, ablakok áthúzására éppenséggel nem képes, de így is kényelmes segítség a több számítógép elõtt dolgozók számára.
Az elégedetlenségem oka az volt, hogy - bár egy switch-elt LAN-ban vagyok a vnc-t futtató géppel - elõfordul, hogy újraindítom, lefagy, kirúgom a kábelt, tehát megszakad az x2vnc hálózati kapcsolata és ilyenkor az egérmutatóm és vele együtt a gépelési fókusz ottmarad a semmiben! Az x2vnc várja, amíg a hálózati stack kézbesíti a legutóbbi egérmozgató parancsát...
Elõször gondoltam, majd a TCP socket-ot okosítom meg mondván "haver, kettõ szegmens retransmitt után hagyd a fenébe, mert az a peer halott!". Persze nem rendszerszinten alkalmaztam volna, csak az x2vnc által nyitott socket-ekre.
Ennél sokkal egyszerũbbnek bizonyult a következõ:

<pre>
ssize_t write(int fd, const void *buf, size_t count)
{
        int (*real_write)(int fd, const void *buf, size_t count) = NULL;
        int real_write_return;
        int alarm_sec = 2;
        /* ... */
        alarm(alarm_sec);
        real_write_return = real_write(fd, buf, count);
        alarm(0);
        return real_write_return;
}
</pre>

A program végsõ soron a write(2) hívást használja, hogy a hálózatra adatot küldjön. Meghatároztam egy kettõ másodperces türelmi idõt (alarm_sec változó), ameddig a rendszerhívásban tartózkodhat. Az alarm() függvénnyel húzom fel az ''ébresztõórát'' és amikor csörög, a folyamatszál kap egy SIGALRM-ot én pedig visszakapom az irányítást (és lecsapom a wekkert: alram(0)).

A teljes kódért nyisd meg a csatolt fájlt.
