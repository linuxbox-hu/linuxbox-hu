---
excerpt: "<style>\r\ncode {background-color:black;color:limegreen;font-weight:bold}\r\n.block
  {display:block}\r\n</style>\r\nHadd kedveskedjek a <font color=red style=\"background-color:gold;font-variant:small-caps\"><b>Linuxbox</b></font>
  olvasóinak egy kis konzolos segédprogrammal!\r\n\r"
categories: []
layout: blog
author: bAndie91
title: Jobb taszkkezelõ
created: 1325387158
---
<style>
code {background-color:black;color:limegreen;font-weight:bold}
.block {display:block}
</style>
Hadd kedveskedjek a <font color=red style="background-color:gold;font-variant:small-caps"><b>Linuxbox</b></font> olvasóinak egy kis konzolos segédprogrammal!

A parancsterminál felületét alapjában véve egyetlen alkalmazás foglalja el, a shell. Azonban sok megoldás létezik még a grafikus ablakkezelõ elõtt is, amivel a konzolból munkaasztalt varázsolhatunk. Ilyen pl. a <b>GNU screen</b>, vagy a <b>tmux</b> terminál többszörözõ; válthatunk másik <b>vty</b>-re; vagy kicsit hasonlóak a háttérshellt használó programok, ahol a célprogramban végezzük gyakori mũveleteket (pl fájlkezelés <b>mc</b>-vel), <i>minden másra pedig ott a shell</i>. 
A legtöbb shellnek van viszont beépített job kezelõje és különben is szeretem a már meglévõ megoldásokat használni! <b>bash</b>-ben így fest a feladatkezelõ:
<ul>
<li>indíthatom a parancsokat a háttérben
<code>$ find / -iname afajlaminemtudomholislehet &</code></li>
<li>futó programot pillanatmegállíthatok, hogy visszakapjam a promptot
<code>Ctrl-Z</code></li>
<li>majd a háttérben továbbfuttatom
<code>$ bg %1</code></li>
<li>Milyen taszkjaim is vannak?
<code>$ jobs</code></li>
<li>újra elõveszem az elõtérbe
<code>$ fg %1</code></li>
</ul>

Ezzel a pár rövidke <i>builtin</i> paranccsal kezelem a bash beépített feladatkezelõjét. Habár igen rövidek, sõt még így is rövidíteni lehet (<code>fg %+</code> = <code>fg</code> = <code>%+</code>, <code>bg %1</code> = <code>%1&</code>), jól jönne hozzá egy <b>jobb</b> job kezelõ!

Erre írtam a <b>jobsel</b> «job select» szkriptet. 
<ol>
<li>Kezdetben csak egy promptban megjelenõ szám volt, ami a háttérben futó job-ok számáról tájékoztatott. 
<code class=block>PS1='\[\033[${PS1COLOR_USER}m\]\u\[\033[${PS1COLOR_AT}m\]@\[\033[${PS1COLOR_HOST}m\]\h$(ERRORLEVEL=$?; test \j -eq 0 || echo -n "\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_JOBS}m\]\j"; test $ERRORLEVEL -eq 0 || echo -n "\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_EXITCODE}m\]$ERRORLEVEL")\[\033[${PS1COLOR_DELIM1}m\]:\[\033[${PS1COLOR_WD}m\]\w\[\033[${PS1COLOR_DELIM2}m\]\$\[\033[00m\] '</code></li>
<li>Majd kibõvítettem a PROMPT_COMMAND-omat, ahogyan <a href=/node/631#comment-985>kecsi javasolta</a>:
<code>PROMPT_COMMAND="$PROMPT_COMMAND${PROMPT_COMMAND:+; }"'jobs -l | _jobs_on_prompt'</code>
Ahol a _jobs_on_prompt ez a <i>perl egysoros</i>:
<code class=block><font color="#ffff00"><b>while</b></font>(&lt;&gt;){ (<font color="#00ffff"><b>$j</b></font>,<font color="#00ffff"><b>$p</b></font>)=<font color="#ffff00"><b>/</b></font><font color="#ff6060"><b>(</b></font><font color="#ff6060"><b>\d</b></font><font color="#ff6060"><b>+)</b></font><font color="#ff6060"><b>\]\S</b></font><font color="#ff6060"><b>?</b></font><font color="#ff6060"><b>\s</b></font><font color="#ff6060"><b>+(</b></font><font color="#ff6060"><b>\d</b></font><font color="#ff6060"><b>+)</b></font><font color="#ffff00"><b>/</b></font>; <font color="#ffff00"><b>open</b></font>(<font color="#00ffff"><b>P</b></font>,<font color="#ff40ff"><b>&quot;</b></font><font color="#ff40ff"><b>/proc/</b></font><font color="#00ffff"><b>$p</b></font><font color="#ff40ff"><b>/stat</b></font><font color="#ff40ff"><b>&quot;</b></font>) <font color="#ffff00"><b>and</b></font>&nbsp;(<font color="#00ffff"><b>$c</b></font>,<font color="#00ffff"><b>$s</b></font>)=(<font color="#00ffff"><b>&lt;P&gt;</b></font>=~<font color="#ffff00"><b>/</b></font><font color="#ff6060"><b>\s\(</b></font><font color="#ff6060"><b>(.+?)</b></font><font color="#ff6060"><b>\)\s</b></font><font color="#ff6060"><b>+(</b></font><font color="#ff6060"><b>\S</b></font><font color="#ff6060"><b>+)</b></font><font color="#ffff00"><b>/</b></font>) <font color="#ffff00"><b>and</b></font>&nbsp;<font color="#00ffff"><b>$o</b></font>.=<font color="#ff40ff"><b>&quot;</b></font><font color="#ff40ff"><b>[%</b></font><font color="#00ffff"><b>$j</b></font><font color="#ff40ff"><b>&nbsp;</b></font><font color="#00ffff"><b>$c</b></font><font color="#ff40ff"><b>(</b></font><font color="#00ffff"><b>$p</b></font><font color="#ff40ff"><b>) </b></font><font color="#00ffff"><b>$s</b></font><font color="#ff40ff"><b>] </b></font><font color="#ff40ff"><b>&quot;</b></font>} <font color="#ffff00"><b>print</b></font>&nbsp;<font color="#ff40ff"><b>&quot;</b></font><font color="#ff6060"><b>\033</b></font><font color="#ff40ff"><b>[s</b></font><font color="#ff6060"><b>\033</b></font><font color="#ff40ff"><b>[1;0H</b></font><font color="#ff6060"><b>\033</b></font><font color="#ff40ff"><b>[</b></font><font color="#00ffff"><b>$ENV</b></font><font color="#00ffff"><b>{</b></font><font color="#ff40ff"><b>PS1COLOR_JOBS</b></font><font color="#00ffff"><b>}</b></font><font color="#ff40ff"><b>mjobs: </b></font><font color="#00ffff"><b>$o</b></font><font color="#ff6060"><b>\033</b></font><font color="#ff40ff"><b>[m</b></font><font color="#ff6060"><b>\033</b></font><font color="#ff40ff"><b>[u</b></font><font color="#ff40ff"><b>&quot;</b></font>&nbsp;<font color="#ffff00"><b>if</b></font><font color="#00ffff"><b>$.</b></font></code>
A legfelsõ konzolsorba sorolja fel a job-okat.</li>
<li>Most pedig ott áll a dolog, hogy ha már ilyen szép tálcagomb-szerũen csücsülnek fenn a futó programok, tegyük interaktívvá és lehessen õket kiválasztani!
Ehhez már egy egysorosnál hosszabb kódot tudtam gyártani (bár CRLF nélkül is meg lehetne írni ;) 
A cikk csatolmányaként tudjátok letölteni!
Kis HaszUtMelléMaFor:
Ha lementetted valahova a $PATH-ba jobsel néven futtathatósági joggal,
<ul>
<li>érdemes rá <b>alias</b>t deklarálni:
<code>alias j='eval $(jobsel "$(jobs -l)" $COLUMNS)'</code>, </li>
<li>vagy <b>keybinding</b>et mondjuk a Meta-j billentyũkombinációhoz:
<code>bind -x '"\204"':"eval \$(jobsel \"\$(jobs -l)\" \$COLUMNS)"
bind '"\ej"':"\"\204\""</code></li>
</ul>
Innen már boldogulsz, jobbra-balra kiválaszt, enter "megnyit", kérdõjel súgó.
</ol>

Köszönöm, jó hekkelést!
