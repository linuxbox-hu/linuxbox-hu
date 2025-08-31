---
excerpt: "A következő: tiffrecompress, egy apró script, pl a gimp separate pluginja
  által előállított tiff fájlok tömörítéséhez, a kimeneti fájl LZW tömörítést kap,
  és lzw.tiff kiterjesztést. A libtiff csomag tiffcp parancsát használja, felület
  szintén zenity, de nem is kellene :-)\r\nA kód:\r\n<code>#!/bin/bash \r\n#################################################\r"
categories: []
layout: blog
author: batyu
mail: batyuu@gmail.com
title: Multimédia scriptek IV.
created: 1263659431
---
A következő: tiffrecompress, egy apró script, pl a gimp separate pluginja által előállított tiff fájlok tömörítéséhez, a kimeneti fájl LZW tömörítést kap, és lzw.tiff kiterjesztést. A libtiff csomag tiffcp parancsát használja, felület szintén zenity, de nem is kellene :-)
A kód:
<code>#!/bin/bash 
#################################################
# Script to recompress any tiff image file to LZW compressed tiff.
# This script does not modify the file which you select, it creates a new file.
# It cannot convert a directory but you can select several files.
#################################################
#		INFO
# Author : Batyu'
# Licence : GNU GPL
# Dependency
#		zenity
#		tiffcp (libtiff package)
# Based on
#		WOM_audioconverter
# History
#		15.01.2010 : v0.1 : First public version
# Install
# 		Put on ~/.gnome2/nautilus-scripts/ or any other directory under $HOME ($HOME/.scripts)
#		In a console : chmod u+x ~/.gnome2/nautilus-scripts/tiffrecompress.sh
#		Optional: add thunar custom actions...


version="0.1"
#################################################
#
###### Default = English #####
		title="tiffrecompresslzw "$version""
		pleasesel="Please select at least one file."
		noselec=""$title" recompress tiff to LZW tiff. "$pleasesel""
		nobin="Program tiffcp (libtiff) is not installed, please install !"
		warning="Warning"
		Working="Working"
		Done="Done!"
	case $LANG in
	######## Magyarul #########
		hu* )
		title=" "$version""
		pleasesel="Kérlek válassz ki legalább 1 fájlt!"
		noselec=""$title" script tiff képfájlok LZW tömörítéséhez. "$pleasesel""
		warning="Figyelem"
		nobin="A tiffcp (libtiff) nem található, telepítsd!"
		Working="Készül a"
		Done="Az exportálás kész!" ;;
	esac

#################################
#	PROGRAM						#
######## Test dependency ########

which tiffcp 2>/dev/null
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


######## Recompressing ########
while [ $# -gt 0 ]; do
	infile=$1
	lzw_file=`echo "$infile" | sed 's/\.\w*$/.lzw.tiff/'`
	tiffcp -c lzw "$infile" "$lzw_file" | zenity --progress --text="$Working $lzw_file" --pulsate --auto-close && zenity --info --text="$Done"
	shift
done

</code>
