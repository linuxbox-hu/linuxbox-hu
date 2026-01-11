---
layout: post
title: Újra bash - Szines fájlnévkiegészítés!
date: 2014-05-27
author: bAndie91
categories: [linux]
tags: bash, zsh, color, completion
excerpt: Az alábbi szkript egy függvényt tartalmaz, amivel lehetőségünk van **bash** alatt a zsh-tól olyannyira irigyelt színes tab completion-t szimulálni.
---
Az alábbi szkript egy függvényt tartalmaz, amivel lehetőségünk van **bash** alatt a [zsh](http://zsh.sourceforge.net/)-tól olyannyira irigyelt színes tab completion-t szimulálni.
Telepítése két lépésből áll:

1. beolvastatni a fájlt, létrehozva ezzel a 'color_completion' függvényt:  
   `. color_completion.sh`  
   ne felejtsük a .bash_profile / .bashrc megfelelő szakaszába is beszúrni, ha megtetszett és tartósan is használni akarjuk
2. társítani egy billentyűhöz, mint ahogyan a Tab megnyomásával a beépített kiegézítőt érjük el:  
   `bind -x '"\234":color_completion $READLINE_POINT "$READLINE_LINE"'`  
   `bind '"\eOQ":"\234"'`  
   A `\234` oktális szám egy szabadon választott keycode, ami még nincs lefoglalva; az `\eOQ` pedig egy ANSI szekvencia, ami az én xterm-emen az F2-nek felel meg. Az egyes funkcióbillentyűk ANSI kódját úgy deríthetjük ki, hogy sima parancssorban megnyomjuk a `Ctrl-V`-t, majd a vizsgált billentyűt. Fogunk látni két karaktert: `~[`, ez az ESC karakter megjelenése, a parancsban `\e`-t írjunk helyette. Biztos jobban kézreesik, ha a Tab-hoz rendeljük hozzá a szkriptünket (ekkor `\eOQ` helyett `\C-I` kell) - elvileg lehetséges, de nem próbáltam. A beépített kiegészítőt meg mondjuk a `Shift-Tab`-hoz (`\e[Z`) vagy fordítva...

**Képességei:**
- A bash-nél megszokott módon kezeli a symlinkeket
- A szinezés az ls(1) működését követi - ugyanis belsőleg azt hívja -, az `$LS_COLORS` változó szerkesztésével módosítható

**Hiányosságai:**
- Kevésbé okos a mezőelválasztók ügyében (fixen szóköz és egyenlőségjel)
- Egyelőre még nem olyan funkciógazdag, mint a zsh vagy maga a bash tabkiegészítő alprogramja - mivel ez a függvény teljesen független a beépített completion képességtől, nem is pluginolható

**Plusz funkciói:**
- Kevés fájlnál részletes listát ad (`ls -l`), sok fájl esetén többoszlopos üzemmódba vált
- Tudja a tilde – home könyvtár behelyettesítést

```bash
#!/bin/bash
#
# Colour filename completion for bash.
# Release 6
#
# How To Install:
#
#  + source this file implementing 'color_completion' function
#
#     $ source color_completion.sh
#
#  + bind a function key to run this command
#
#     $ bind -x '"\234":color_completion $READLINE_POINT "$READLINE_LINE"'
#     $ bind '"\eOQ":"\234"'
#
#    where \234 is a random unused keycode, and \eOQ is the ANSI sequence
#    of F2 under xterm. To find ANSI codes of each key, press Ctrl-V
#    followed by the desired key in the commandline.
#
# Require bash version 4
#

color_completion() {
	local rl_pos=\$1
	shift
	local rl_str=$@

	local word=${rl_str:0:$rl_pos}
	word=${word##* }
	word=${word##*=}

	local save_nullglob
	local save_nocaseglob
	shopt nullglob >/dev/null && save_nullglob=s || save_nullglob=u
	shopt nocaseglob >/dev/null && save_nocaseglob=s || save_nocaseglob=u
	shopt -s nullglob
	shopt -u nocaseglob

	local list
	declare -a list
	local xword=$word
	local retrostute
	declare -A retrostute
	if expr "$word" : '~/'>/dev/null; then
		xword="$HOME${word:1}"
		retrostute[tilde]=${#HOME}
	fi
	list=("$xword"*)

	if [ "${#list[@]}" = 0 ]; then
		echo -ne "\a"

	elif [ "${#list[@]}" = 1 ]; then
		local match=${list[0]}
		local newword=$match
		local k
		for k in "${!retrostute[@]}"; do
			case "$k" in
			tilde)
				newword="~${newword:${retrostute[$k]}}"
				;;
			esac
		done
		if [ -d "$match" ]; then
			if [ ! -L "$match" -o "$word" = "$newword" ]; then
				newword="$newword/"
			fi
		else
			newword="$newword "
		fi

		READLINE_LINE="${READLINE_LINE:0:$(($rl_pos - ${#word}))}$newword${READLINE_LINE:$rl_pos}"
		READLINE_POINT=$(($rl_pos - ${#word} + ${#newword}))

	else
		local basedir=
		expr "${list[0]}" : '.*/' >/dev/null && basedir=${list[0]%/*}
		local dirname=`dirname "${list[0]}"`
		local z=${#list[@]}
		local i
		local min=-1
		for ((i=0; i<z; i++)); do
			# save basenames
			list[$i]=${list[$i]##*/}
			# find shortest word
			[ $min = -1 -o $min -gt ${#list[$i]} ] && min=${#list[$i]}
		done
		(
		  cd "$dirname"
		  echo -e "\033[;1mfiles:\033[m $word*"
		  if [ ${#list[@]} -lt "${LINES:-0}" ]; then
		  	command ls $LS_OPTIONS -lFd "${list[@]}"
		  else
		  	command ls $LS_OPTIONS -CFd "${list[@]}"
		  fi
		)
		# find common part of words
		local k
		for ((i=1; i<z; i++)); do
			for ((k=0; k<min; k++)); do
				[ "${list[$i]:$k:1}" != "${list[$((i-1))]:$k:1}" ] && break
			done
			[ $min -gt $k ] && min=$k
			[ $min = 0 ] && break
		done
		local ngivenpart=${#xword}
		[ -n "$basedir" ] && ngivenpart=$((ngivenpart - ${#basedir} - 1))
		let min-=ngivenpart
		[ $min -lt 0 ] && min=0
		local commonpart=${list[0]:$ngivenpart:$min}
		READLINE_LINE="${READLINE_LINE:0:$rl_pos}$commonpart${READLINE_LINE:$rl_pos}"
		READLINE_POINT=$(($rl_pos + ${#commonpart}))
	fi

	shopt -$save_nullglob nullglob
	shopt -$save_nocaseglob nocaseglob
}
```
