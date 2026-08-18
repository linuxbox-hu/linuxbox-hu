---
author: bAndie91
categories: []
created: 1325387158
date: '2012-01-01T00:00:00Z'
title: Jobb taszkkezelõ
aliases:
- /blog/706/
- /node/706/
---
Hadd kedveskedjek a **Linuxbox** olvasóinak egy kis konzolos segédprogrammal!

A parancsterminál felületét alapjában véve egyetlen alkalmazás foglalja el, a shell. Azonban sok megoldás létezik még a grafikus ablakkezelõ elõtt is, amivel a konzolból munkaasztalt varázsolhatunk. Ilyen pl. a `GNU screen`, vagy a `tmux` terminál többszörözõ; válthatunk másik `vty`-re; vagy kicsit hasonlóak a háttérshellt használó programok, ahol a célprogramban végezzük gyakori mũveleteket (pl fájlkezelés `mc`-vel), *minden másra pedig ott a shell*.
A legtöbb shellnek van viszont beépített job kezelõje és különben is szeretem a már meglévõ megoldásokat használni! `bash`-ben így fest a feladatkezelõ:

- indíthatom a parancsokat a háttérben
  `$ find / -iname afajlaminemtudomholislehet &`
- futó programot pillanatmegállíthatok, hogy visszakapjam a promptot
  `Ctrl-Z`
- majd a háttérben továbbfuttatom
  `$ bg %1`
- Milyen taszkjaim is vannak?
  `$ jobs`
- újra elõveszem az elõtérbe
  `$ fg %1`

Ezzel a pár rövidke *builtin* paranccsal kezelem a bash beépített feladatkezelõjét. Habár igen rövidek, sõt még így is rövidíteni lehet (`fg %+` = `fg` = `%+`, `bg %1` = `%1&`), jól jönne hozzá egy **jobb** job kezelõ!

Erre írtam a **jobsel** «job select» szkriptet.

1. Kezdetben csak egy promptban megjelenõ szám volt, ami a háttérben futó job-ok számáról tájékoztatott.
   ```bash
   PS1='\[\033[${PS1COLOR_USER}m\]\u\[\033[${PS1COLOR_AT}m\]@\[\033[${PS1COLOR_HOST}m\]\h$(ERRORLEVEL=$?; test \j -eq 0 || echo -n "\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_JOBS}m\]\j"; test $ERRORLEVEL -eq 0 || echo -n "\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_EXITCODE}m\]$ERRORLEVEL")\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_WD}m\]\w\[\033[${PS1COLOR_DELIM2}m\]\$\[\033[00m\] '
   ```
2. Majd kibõvítettem a PROMPT_COMMAND-omat, ahogyan [kecsi javasolta](/node/631#comment-985):
   `PROMPT_COMMAND="$PROMPT_COMMAND${PROMPT_COMMAND:+; }"'jobs -l | _jobs_on_prompt'`
   Ahol a _jobs_on_prompt ez a *perl egysoros*:
   ```perl
   while(<>){ ($j,$p)=/(\d+)\]\S?\s+(\d+)/; open(P,"/proc/$p/stat") and ($c,$s)=(<P>=~/\s\((.+?)\)\s+(\S+)/) and $o.="[%$j $c($p) $s] "} print "\033[s\033[1;0H\033[$ENV{PS1COLOR_JOBS}mjobs: $o\033[m\033[u" if$.
   ```
   A legfelsõ konzolsorba sorolja fel a job-okat.
3. Most pedig ott áll a dolog, hogy ha már ilyen szép tálcagomb-szerũen csücsülnek fenn a futó programok, tegyük interaktívvá és lehessen õket kiválasztani!
   Ehhez már egy egysorosnál hosszabb kódot tudtam gyártani (bár CRLF nélkül is meg lehetne írni ;)
   A cikk csatolmányaként tudjátok letölteni!
   Kis HaszUtMelléMaFor:
   Ha lementetted valahova a $PATH-ba jobsel néven futtathatósági joggal,
   - érdemes rá **alias**t deklarálni:
     `alias j='eval $(jobsel "$(jobs -l)" $COLUMNS)'`,
   - vagy **keybinding**et mondjuk a Meta-j billentyũkombinációhoz:
     ```bash
     bind -x '"\204"':"eval \$(jobsel \"\$(jobs -l)\" \$COLUMNS)"
     bind '"\ej"':"\"\204\""
     ```

   Innen már boldogulsz, jobbra-balra kiválaszt, enter "megnyit", kérdõjel súgó.

Köszönöm, jó hekkelést!
