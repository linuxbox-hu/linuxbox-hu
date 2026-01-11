---
excerpt: "Pár script, ami hasznos lehet, meg hogy meglegyen itt is.\r\nmp4audioextract:
  faad segítségével kinyeri az aac hangot. Thunar egyéni műveletként kényelmes használni,
  zenity alapú egyszerű felületen megy.\r\nMivel csatolni nem nagyon lehet, a kód:\r\n<code>\r\n#!/bin/bash
  \r\n#################################################\r\n# Script to extract aac
  audio from mp4 video\r"
categories: []
layout: blog
author: batyu
title: multimédia scriptek
created: 1263658521
---
Pár script, ami hasznos lehet, meg hogy meglegyen itt is.
mp4audioextract: faad segítségével kinyeri az aac hangot. Thunar egyéni műveletként kényelmes használni, zenity alapú egyszerű felületen megy.
Mivel csatolni nem nagyon lehet, a kód:
<code>
#!/bin/bash 
#################################################
# Script to extract aac audio from mp4 video
# mp4extracttoaac does not modify the file which you select, it creates a new file.
# It cannot convert a directory but you can select several files.
#################################################
#		INFO
# Author : Batyu'
# Licence : GNU GPL
# Dependency
#		zenity
#		faad
# Based on
#		WOM_audioconverter
# History
#		15.01.2010 : v0.1 : First public version
# Install
# 		Put on ~/.gnome2/nautilus-scripts/ or any other directory under $HOME ($HOME/.scripts)
#		In a console : chmod u+x ~/.gnome2/nautilus-scripts/
#		Optional: add thunar custom actions...


version="0.1"
#################################################
#
###### Default = English #####
		title="mp4audioextract "$version""
		pleasesel="Please select at least one file."
		noselec=""$title" extract aac stream from mp4. "$pleasesel""
		nobin="Program faad is not installed, please install !"
		warning="Warning"
		Working="Working"
		Done="Done!"
	case $LANG in
	######## Magyarul #########
		hu* )
		title="mp4audioextract "$version""
		pleasesel="Kérlek válassz ki legalább 1 fájlt!"
		noselec=""$title" script aac audió kinyerésére mp4-ből. "$pleasesel""
		warning="Figyelem"
		nobin="A faad nem található, telepítsd!"
		Working="Készül a"
		Done="Az exportálás kész!" ;;
	esac

#################################
#	PROGRAM						#
######## Test dependency ########

which faad 2>/dev/null
if [ $? != 0 ]
then
	zenity --error --title="$title" --text="$nobin"
	exit 0
fi

#### file selection test ###
if [ $# -eq 0 ]; then
	zenity --error --title="$warning" --text="$noselec"
	exit 1
fi


######## Extract aac ########
while [ $# -gt 0 ]; do
	infile=$1
	aac_file=`echo "$infile" | sed 's/\.\w*$/.aac/'`
	faad -a "$aac_file" "$infile" | zenity --progress --text="$Working $aac_file" --pulsate --auto-close && zenity --info --text="$Done"
	shift
done

</code>
