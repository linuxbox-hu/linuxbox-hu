---
excerpt: "<style>\r\ncode {\r\nfont-family: monospace; color: #fff; background-color:
  #000; font-weight: bold;\r\n}\r\n</style>\r\n<p>\r\nAz alábbi szkript egy függvényt
  tartalmaz, amivel lehetőségünk van <b>bash</b> alatt a <a href='http://zsh.sourceforge.net/'>zsh</a>tól
  olyannyira irigyelt színes tab completion-t szimulálni.\r\nTelepítése két lépésből
  áll:\r\n"
categories: []
layout: blog
author: bAndie91
mail: bandie9100@freemail.hu
title: Újra bash - Szines fájlnévkiegészítés!
created: 1401192864
---
<style>
code {
font-family: monospace; color: #fff; background-color: #000; font-weight: bold;
}
</style>
<p>
Az alábbi szkript egy függvényt tartalmaz, amivel lehetőségünk van <b>bash</b> alatt a <a href='http://zsh.sourceforge.net/'>zsh</a>tól olyannyira irigyelt színes tab completion-t szimulálni.
Telepítése két lépésből áll:
<!--break-->
<ol>
<li>
       beolvastatni a fájlt, létrehozva ezzel a 'color_completion' függvényt:<br>
       <code>. color_completion.sh</code><br>
       ne felejtsük a .bash_profile / .bashrc megfelelő szakaszába is beszúrni, ha megtetszett és tartósan is használni akarjuk</li>
<li>
       társítani egy billentyűhöz, mint ahogyan a Tab megnyomásával a beépített kiegézítőt érjük el:<br>
       <code>bind -x '"\234":color_completion $READLINE_POINT "$READLINE_LINE"'</code><br>
       <code>bind '"\eOQ":"\234"'</code><br>
       A <code>\234</code> oktális szám egy szabadon választott keycode, ami még nincs lefoglalva; az <code>\eOQ</code> pedig egy ANSI szekvencia, ami az én xterm-emen az F2-nek felel meg. Az egyes funkcióbillentyűk ANSI kódját úgy deríthetjük ki, hogy sima parancssorban megnyomjuk a <code>Ctrl-V</code>-t, majd a vizsgált billentyűt. Fogunk látni két karaktert: <code>~[</code>, ez az ESC karakter megjelenése, a parancsban <code>\e</code>-t írjunk helyette. Biztos jobban kézreesik, ha a Tab-hoz rendeljük hozzá a szkriptünket (ekkor <code>\eOQ</code> helyett <code>\C-I</code> kell) - elvileg lehetséges, de nem próbáltam. A beépített kiegészítőt meg mondjuk a <code>Shift-Tab</code>-hoz (<code>\e[Z</code>) vagy fordítva...
</li>
</ol>
</p>

Képességei:
<ul>
<li>A bash-nél megszokott módon kezeli a symlinkeket</li>
<li>A szinezés az ls(1) működését követi - ugyanis belsőleg azt hívja -, az $LS_COLORS változó szerkesztésével módosítható</li>
</ul>

Hiányosságai:
<ul>
<li>Kevésbé okos a mezőelválasztók ügyében (fixen szóköz és egyenlőségjel)</li>
<li>Egyelőre még nem olyan funkciógazdag, mint a zsh vagy maga a bash tabkiegészítő alprogramja - mivel ez a függvény teljesen független a beépített completion képességtől, nem is pluginolható</li>
</ul>

Plusz funkciói:
<ul>
<li>Kevés fájlnál részletes listát ad (ls -l), sok fájl esetén többoszlopos üzemmódba vált</li>
<li>Tudja a tilde &ndash; home könyvtár behelyettesítést</li>
</ul>

<style type="text/css">
<!--
pre { white-space: pre-wrap; font-family: monospace; color: #fff; background-color: #000; }
.lnr { color: #ffff00; }
.Special { color: #ff40ff; }
.Constant { color: #ff6060; }
.PreProc { color: #ff40ff; }
.Statement { color: #ffff00; }
.Identifier { color: #00ffff; }
.Comment { color: #8080ff; }
-->
</style>

<pre>
<span class="Comment">#!/bin/bash</span>
<span class="Comment">#</span>
<span class="Comment"># Colour filename completion for bash.</span>
<span class="Comment"># Release 6</span>
<span class="Comment">#</span>
<span class="Comment"># How To Install:</span>
<span class="Comment">#</span>
<span class="Comment">#  + source this file implementing 'color_completion' function</span>
<span class="Comment">#</span>
<span class="Comment">#     $ source color_completion.sh</span>
<span class="Comment">#</span>
<span class="Comment">#  + bind a function key to run this command</span>
<span class="Comment">#</span>
<span class="Comment">#     $ bind -x '&quot;\234&quot;:color_completion $READLINE_POINT &quot;$READLINE_LINE&quot;'</span>
<span class="Comment">#     $ bind '&quot;\eOQ&quot;:&quot;\234&quot;'</span>
<span class="Comment">#</span>
<span class="Comment">#    where \234 is a random unused keycode, and \eOQ is the ANSI sequence</span>
<span class="Comment">#    of F2 under xterm. To find ANSI codes of each key, press Ctrl-V</span>
<span class="Comment">#    followed by the desired key in the commandline.</span>
<span class="Comment">#</span>
<span class="Comment"># Require bash version 4</span>
<span class="Comment">#</span>

<span class="Identifier">color_completion() {</span>
	<span class="Statement">local</span> <span class="Identifier">rl_pos</span>=<span class="PreProc">$1</span>
	<span class="Statement">shift</span>
	<span class="Statement">local</span> <span class="Identifier">rl_str</span>=<span class="PreProc">$@</span>

	<span class="Statement">local</span> <span class="Identifier">word</span>=<span class="PreProc">${</span><span class="PreProc">rl_str</span><span class="Statement">:</span><span class="Constant">0</span><span class="Statement">:</span><span class="PreProc">$rl_pos</span><span class="PreProc">}</span>
	<span class="Identifier">word</span>=<span class="PreProc">${</span><span class="PreProc">word</span><span class="Statement">##</span>* <span class="PreProc">}</span>
	<span class="Identifier">word</span>=<span class="PreProc">${</span><span class="PreProc">word</span><span class="Statement">##</span>*=<span class="PreProc">}</span>

	<span class="Statement">local</span> save_nullglob
	<span class="Statement">local</span> save_nocaseglob
	<span class="Statement">shopt</span> nullglob <span class="Statement">&gt;</span>/dev/null <span class="Statement">&amp;&amp;</span> <span class="Identifier">save_nullglob</span>=s <span class="Statement">||</span> <span class="Identifier">save_nullglob</span>=u
	<span class="Statement">shopt</span> nocaseglob <span class="Statement">&gt;</span>/dev/null <span class="Statement">&amp;&amp;</span> <span class="Identifier">save_nocaseglob</span>=s <span class="Statement">||</span> <span class="Identifier">save_nocaseglob</span>=u
	<span class="Statement">shopt</span> <span class="Special">-s</span> nullglob
	<span class="Statement">shopt</span> <span class="Special">-u</span> nocaseglob

	<span class="Statement">local</span> list
	<span class="Statement">declare</span><span class="Identifier"> </span><span class="Special">-a</span><span class="Identifier"> list</span>
	<span class="Statement">local</span> <span class="Identifier">xword</span>=<span class="PreProc">$word</span>
	<span class="Statement">local</span> retrostute
	<span class="Statement">declare</span><span class="Identifier"> </span><span class="Special">-A</span><span class="Identifier"> retrostute</span>
	<span class="Statement">if </span><span class="Statement">expr</span> <span class="Statement">&quot;</span><span class="PreProc">$word</span><span class="Statement">&quot;</span> : <span class="Statement">'</span><span class="Constant">~/</span><span class="Statement">'</span> <span class="Statement">&gt;</span>/dev/null<span class="Statement">;</span> <span class="Statement">then</span>
		<span class="Identifier">xword</span>=<span class="Statement">&quot;</span><span class="PreProc">$HOME</span><span class="PreProc">${</span><span class="PreProc">word</span><span class="Statement">:</span><span class="Constant">1</span><span class="PreProc">}</span><span class="Statement">&quot;</span>
		retrostute<span class="Statement">[</span>tilde<span class="Statement">]</span><span class="Statement">=</span><span class="PreProc">${#</span><span class="PreProc">HOME</span><span class="PreProc">}</span>
	<span class="Statement">fi</span>
	<span class="Identifier">list</span>=(<span class="Statement">&quot;</span><span class="PreProc">$xword</span><span class="Statement">&quot;</span>*)


	<span class="Statement">if </span><span class="Statement">[</span> <span class="Statement">&quot;</span><span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span> <span class="Statement">=</span> <span class="Constant">0</span> <span class="Statement">]</span><span class="Statement">;</span> <span class="Statement">then</span>
		<span class="Statement">echo</span><span class="Constant"> -ne </span><span class="Statement">&quot;</span><span class="Special">\a</span><span class="Statement">&quot;</span>

	<span class="Statement">elif</span> <span class="Statement">[</span> <span class="Statement">&quot;</span><span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span> <span class="Statement">=</span> <span class="Constant">1</span> <span class="Statement">]</span><span class="Statement">;</span> <span class="Statement">then</span>
		<span class="Statement">local</span> <span class="Identifier">match</span>=<span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="Constant">0</span><span class="PreProc">]</span><span class="PreProc">}</span>
		<span class="Statement">local</span> <span class="Identifier">newword</span>=<span class="PreProc">$match</span>
		<span class="Statement">local</span> k
		<span class="Statement">for </span>k <span class="Statement">in</span> <span class="Statement">&quot;</span><span class="PreProc">${!</span><span class="PreProc">retrostute</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span><span class="Statement">;</span> <span class="Statement">do</span>
			<span class="Statement">case</span> <span class="Statement">&quot;</span><span class="PreProc">$k</span><span class="Statement">&quot;</span> <span class="Statement">in</span>
			tilde<span class="Statement">)</span>
				<span class="Identifier">newword</span>=<span class="Statement">&quot;</span><span class="Constant">~</span><span class="PreProc">${</span><span class="PreProc">newword</span><span class="Statement">:</span><span class="PreProc">${</span><span class="PreProc">retrostute</span><span class="PreProc">[</span><span class="PreProc">$k</span><span class="PreProc">]</span><span class="PreProc">}}</span><span class="Statement">&quot;</span>
				<span class="Statement">;;</span>
			<span class="Statement">esac</span>
		<span class="Statement">done</span>
		<span class="Statement">if </span><span class="Statement">[</span> <span class="Statement">-d</span> <span class="Statement">&quot;</span><span class="PreProc">$match</span><span class="Statement">&quot;</span> <span class="Statement">]</span><span class="Statement">;</span> <span class="Statement">then</span>
			<span class="Statement">if </span><span class="Statement">[</span> <span class="Statement">!</span> <span class="Statement">-L</span> <span class="Statement">&quot;</span><span class="PreProc">$match</span><span class="Statement">&quot;</span> <span class="Statement">-o</span> <span class="Statement">&quot;</span><span class="PreProc">$word</span><span class="Statement">&quot;</span> <span class="Statement">=</span> <span class="Constant">&quot;$newword&quot;</span> <span class="Statement">]</span><span class="Statement">;</span> <span class="Statement">then</span>
				<span class="Identifier">newword</span>=<span class="Statement">&quot;</span><span class="PreProc">$newword</span><span class="Constant">/</span><span class="Statement">&quot;</span>
			<span class="Statement">fi</span>
		<span class="Statement">else</span>
			<span class="Identifier">newword</span>=<span class="Statement">&quot;</span><span class="PreProc">$newword</span><span class="Constant"> </span><span class="Statement">&quot;</span>
		<span class="Statement">fi</span>

		<span class="PreProc">READLINE_LINE</span><span class="Statement">=</span><span class="Constant">&quot;${READLINE_LINE:0:$(($rl_pos - ${#word}))}$newword${READLINE_LINE:$rl_pos}&quot;</span>
		<span class="PreProc">READLINE_POINT</span><span class="Statement">=</span><span class="PreProc">$((</span><span class="Special">rl_pos - </span><span class="PreProc">${#</span><span class="PreProc">word</span><span class="PreProc">}</span><span class="Special"> + </span><span class="PreProc">${#</span><span class="PreProc">newword</span><span class="PreProc">}</span><span class="PreProc">))</span>

	<span class="Statement">else</span>
		<span class="Statement">local</span> <span class="Identifier">basedir</span>=
		<span class="Statement">expr</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="Constant">0</span><span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span> : <span class="Statement">'</span><span class="Constant">.*/</span><span class="Statement">'</span> <span class="Statement">&gt;</span>/dev/null <span class="Statement">&amp;&amp;</span> <span class="Identifier">basedir</span>=<span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="Constant">0</span><span class="PreProc">]</span><span class="Statement">%</span>/*<span class="PreProc">}</span>
		<span class="Statement">local</span> <span class="Identifier">dirname</span>=<span class="Special">`dirname </span><span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="Constant">0</span><span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span><span class="Special">`</span>
		<span class="Statement">local</span> <span class="Identifier">z</span>=<span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span>
		<span class="Statement">local</span> i
		<span class="Statement">local</span> <span class="Identifier">min</span>=<span class="Constant">-1</span>
		<span class="Statement">for </span><span class="Special">((</span>i<span class="Statement">=</span><span class="Constant">0</span><span class="Statement">;</span> i<span class="Statement">&lt;</span>z<span class="Statement">;</span> i++<span class="Special">))</span><span class="Statement">;</span> <span class="Statement">do</span>
			<span class="Comment"># save basenames</span>
			list<span class="Statement">[</span><span class="PreProc">$i</span><span class="Statement">]</span><span class="Statement">=</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="PreProc">$i</span><span class="PreProc">]</span><span class="Statement">##</span>*/<span class="PreProc">}</span>
			<span class="Comment"># find shortest word</span>
			<span class="Statement">[</span> <span class="PreProc">$min</span> <span class="Statement">=</span> <span class="Constant">-1</span> <span class="Statement">-o</span> <span class="PreProc">$min</span> <span class="Statement">-gt</span> <span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="PreProc">$i</span><span class="PreProc">]</span><span class="PreProc">}</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Identifier">min</span>=<span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="PreProc">$i</span><span class="PreProc">]</span><span class="PreProc">}</span>
		<span class="Statement">done</span>
		<span class="Statement">(</span>
		  <span class="Statement">cd</span> <span class="Statement">&quot;</span><span class="PreProc">$dirname</span><span class="Statement">&quot;</span>
		  <span class="Statement">echo</span><span class="Constant"> </span><span class="Statement">&quot;</span><span class="Special">^[</span><span class="Constant">[;1mfiles:</span><span class="Special">^[</span><span class="Constant">[m </span><span class="PreProc">$word</span><span class="Constant">*</span><span class="Statement">&quot;</span>
		  <span class="Statement">if </span><span class="Statement">[</span> <span class="PreProc">${#</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span> <span class="Statement">-lt</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">LINES</span><span class="Statement">:-</span>0<span class="PreProc">}</span><span class="Statement">&quot;</span> <span class="Statement">]</span><span class="Statement">;</span> <span class="Statement">then</span>
		  	command <span class="Statement">ls</span> <span class="PreProc">$LS_OPTIONS</span> <span class="Special">-lFd</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span>
		  <span class="Statement">else</span>
		  	command <span class="Statement">ls</span> <span class="PreProc">$LS_OPTIONS</span> <span class="Special">-CFd</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span>@<span class="PreProc">]</span><span class="PreProc">}</span><span class="Statement">&quot;</span>
		  <span class="Statement">fi</span>
		<span class="Statement">)</span>
		<span class="Comment"># find common part of words</span>
		<span class="Statement">local</span> k
		<span class="Statement">for </span><span class="Special">((</span>i<span class="Statement">=</span><span class="Constant">1</span><span class="Statement">;</span> i<span class="Statement">&lt;</span>z<span class="Statement">;</span> i++<span class="Special">))</span><span class="Statement">;</span> <span class="Statement">do</span>
			<span class="Statement">for </span><span class="Special">((</span>k<span class="Statement">=</span><span class="Constant">0</span><span class="Statement">;</span> k<span class="Statement">&lt;</span>min<span class="Statement">;</span> k++<span class="Special">))</span><span class="Statement">;</span> <span class="Statement">do</span>
				<span class="Statement">[</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="PreProc">$i</span><span class="PreProc">]</span><span class="Statement">:</span><span class="PreProc">$k</span><span class="Statement">:</span><span class="Constant">1</span><span class="PreProc">}</span><span class="Statement">&quot;</span> <span class="Statement">!=</span> <span class="Statement">&quot;</span><span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="PreProc">$((</span><span class="Special">i</span><span class="Constant">-1</span><span class="PreProc">))</span><span class="PreProc">]</span><span class="Statement">:</span><span class="PreProc">$k</span><span class="Statement">:</span><span class="Constant">1</span><span class="PreProc">}</span><span class="Statement">&quot;</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Statement">break</span>
			<span class="Statement">done</span>
			<span class="Statement">[</span> <span class="PreProc">$min</span> <span class="Statement">-gt</span> <span class="PreProc">$k</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Identifier">min</span>=<span class="PreProc">$k</span>
			<span class="Statement">[</span> <span class="PreProc">$min</span> <span class="Statement">=</span> <span class="Constant">0</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Statement">break</span>
		<span class="Statement">done</span>
		<span class="Statement">local</span> <span class="Identifier">ngivenpart</span>=<span class="PreProc">${#</span><span class="PreProc">xword</span><span class="PreProc">}</span>
		<span class="Statement">[</span> <span class="Statement">-n</span> <span class="Statement">&quot;</span><span class="PreProc">$basedir</span><span class="Statement">&quot;</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Identifier">ngivenpart</span>=<span class="PreProc">$((</span><span class="Special">ngivenpart - </span><span class="PreProc">${#</span><span class="PreProc">basedir</span><span class="PreProc">}</span><span class="Special"> - </span><span class="Constant">1</span><span class="PreProc">))</span>
		<span class="Statement">let</span> min-<span class="Statement">=</span><span class="Constant">ngivenpart</span>
		<span class="Statement">[</span> <span class="PreProc">$min</span> <span class="Statement">-lt</span> <span class="Constant">0</span> <span class="Statement">]</span> <span class="Statement">&amp;&amp;</span> <span class="Identifier">min</span>=<span class="Constant">0</span>
		<span class="Statement">local</span> <span class="Identifier">commonpart</span>=<span class="PreProc">${</span><span class="PreProc">list</span><span class="PreProc">[</span><span class="Constant">0</span><span class="PreProc">]</span><span class="Statement">:</span><span class="PreProc">$ngivenpart</span><span class="Statement">:</span><span class="PreProc">$min</span><span class="PreProc">}</span>
		<span class="PreProc">READLINE_LINE</span><span class="Statement">=</span><span class="Constant">&quot;${READLINE_LINE:0:$rl_pos}$commonpart${READLINE_LINE:$rl_pos}&quot;</span>
		<span class="PreProc">READLINE_POINT</span><span class="Statement">=</span><span class="PreProc">$((</span><span class="Special">rl_pos + </span><span class="PreProc">${#</span><span class="PreProc">commonpart</span><span class="PreProc">}</span><span class="PreProc">))</span>
	<span class="Statement">fi</span>

	<span class="Statement">shopt</span> -<span class="PreProc">$save_nullglob</span> nullglob
	<span class="Statement">shopt</span> -<span class="PreProc">$save_nocaseglob</span> nocaseglob
<span class="Identifier">}</span>

</pre>
