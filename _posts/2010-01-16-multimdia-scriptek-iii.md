---
excerpt: Akár az előző scriptet kiegészítendő, akár más esetben, szükség lehet egy
  bitkép -> jpeg konverterre. Az itt következő image/graphicsmagick alapú script beállítható
  tömörítéssel és felbontással (dpi) konvertál bármely támogatott formátumot jpeg-be.
  A felület szintén zenity.
categories: []
layout: blog
author: batyu
mail: batyuu@gmail.com
title: Multimédia scriptek III.
created: 1263659165
---
Akár az előző scriptet kiegészítendő, akár más esetben, szükség lehet egy bitkép -> jpeg konverterre. Az itt következő image/graphicsmagick alapú script beállítható tömörítéssel és felbontással (dpi) konvertál bármely támogatott formátumot jpeg-be. A felület szintén zenity. Alapesetben rádiólistán választható a minőség, és graphicsmagick-et használ, de a kódban ott a kommentezett sorokban a lehetőség csúszkás beállításra, és imagemagick használatára.
A kód:
<code>#!/bin/bash
#################################################
# Script to convert image files to jpg
# script does not modify the file which you select, it creates a new file.
# It cannot convert a directory but you can select several files.
# 

#################################################
version="0.1"
#
		###### Default = English #####
		title="any2jpg "$version""
		pleasesel="Please select at least one file."
		noselec=""$title" convert images to jpg. "$pleasesel""
		nobin="Program Imagemagick/Graphicsmagick is not installed, please install !"
		warning="Warning"
		qsel="Quality (%)"
		exportof="jpeg quality setting"
		Resolution="Resolution"
		Working="Working"
		Done="Done!"
	case $LANG in
		######## Magyarul #########
		hu* )
		title="any2jpg "$version""
		pleasesel="Kérlek válassz ki legalább 1 fájlt!"
		noselec=""$title" export script bitképekből jpg-be."$pleasesel""
		warning="Figyelem"
		nobin="Az Imagemagick/Graphicsmagick nem található, telepítsd!"
		qsel="Minőség (%)"
		exportof="jpeg minőség beállítása"
		Resolution="Felbontás (dpi)"
		Working="Készül a"
		Done="Az exportálás kész!" ;;
	esac

#################################################
#	PROGRAM
######## Test dependency ########
which convert 2>/dev/null
if [ $? != 0 ]
then
	zenity --error --title="$title" --text="$nobin"
	exit 0
fi

#### File selection check ###
if [ $# -eq 0 ]; then
	zenity --error --title="$warning" --text="$noselec"
	exit 1
fi

######## quality settings ########
while [ ! "$quality" ]
do
#	quality=`zenity --scale --title "$title" --text="$qsel" --min-value="60" --max-value="100" --value="90" --step 1`
	quality=`zenity --title "$title" --list --radiolist --column="%" --column="$exportof" FALSE "75" FALSE "80" FALSE "85" TRUE  "90" FALSE "92" FALSE "94" FALSE "96" FALSE "100" --text "$qsel"`
	if  [ $? != 0 ]; then
		exit 1
	fi
	[ $? -ne 0 ] && exit 2
done

######## resolution settings ########
while [ ! "$sample" ]
do
	sample=`zenity --title="$title" --list --radiolist --column="" --column="$Resolution:" FALSE "90x90" FALSE "120x120" TRUE "300x300" FALSE "600x600" FALSE "1200x1200"`
	if  [ $? != 0 ]; then
		exit 1
	fi
	[ $? -ne 0 ] && exit 2
done

######## Export jpg ########
while [ $# -gt 0 ]; do
	picture=$1
	jpg_file=`echo "$picture" | sed 's/\.\w*$/.jpg/'`
#   when use imagemagick, you can uncomment the next line, and comment it another. ##
#	/usr/bin/convert -quality "$quality" -set density "$sample" "$picture"  -background white -flatten jpeg:"$jpg_file" | zenity --progress --text="$Working $picture" --percentage=0 --auto-close && zenity --info --text="$Done"
	/usr/bin/gm convert -quality "$quality" -set density "$sample" "$picture"  -background white -flatten jpeg:"$jpg_file" | zenity --progress --text="$Working $picture" --pulsate --auto-close && zenity --info --text="$Done"
	shift
done
</code>
