---
excerpt: "Jöjjön a következő: svg2png. Inkscape-t használ parancsmódban meghívva,
  zenity felületen paraméterezhető, exportált terület és a kimeneti felbontás állítható.\r\nA
  kód:\r\n<code>#!/bin/bash \r\n#################################################\r\n#\tWHAT
  is svg2png ?\r\n# Script to convert svg files to png\r\n# svg2png does not modify
  the file which you select, it creates a new file.\r"
categories: []
layout: blog
author: batyu
title: multimédia scriptek II.
created: 1263658735
---
Jöjjön a következő: svg2png. Inkscape-t használ parancsmódban meghívva, zenity felületen paraméterezhető, exportált terület és a kimeneti felbontás állítható.
A kód:
<code>#!/bin/bash 
#################################################
#	WHAT is svg2png ?
# Script to convert svg files to png
# svg2png does not modify the file which you select, it creates a new file.
# It cannot convert a directory but you can select several files.

#################################################
#		INFO
# Author : yeKcim - yeknan@yahoo.fr - http://yeknan.free.fr
# Licence : GNU GPL
# Dependency
#		zenity
#		inkscape
# Based on
#		WOM_audioconverter
# History
#		15.01.2006 : v0.1 : First public version
# Install
# 		Put on ~/.gnome2/nautilus-scripts/
#		In a console : chmod u+x ~/.gnome2/nautilus-scripts/svg2png

version="0.1"
#################################################
#	TRADUCTIONS
		###### Default = English #####
		title="svg2png "$version""
		pleasesel="Please select at least one file."
		noselec=""$title" converts svg to png. "$pleasesel""
		nobin="Program inkscape is not installed, please install !"
		warning="Warning"
		choix="Export type ?"
		drawing="Drawing"
		canvas="Canvas"
		exportof="Picture to convert :"
		Resolution="Resolution"
		Working="Working"
		Done="Done!"
	case $LANG in
		######## Français ########
		fr* )
		title="svg2png "$version""
		pleasesel="Merci de sélectionner au moins un fichier."
		noselec=""$title" permet de convertir des svg en png. "$pleasesel""
		warning="Attention"
		nobin="Le programme inkscape n'est pas installé, veuillez l'installer !"
		choix="Type d'export ?"
		drawing="Dessin"
		canvas="Page"
		exportof="Image à convertir :"
		Resolution="Resolution"
		Working="Working on"
		Done="Done" ;;
	######## Magyarul #########
		hu* )
		title="svg2png "$version""
		pleasesel="Kérlek válassz ki legalább 1 fájlt!"
		noselec=""$title" export script svg-ből png-be."$pleasesel""
		warning="Figyelem"
		nobin="Az inkscape nem található, telepítsd!"
		choix="Exportálás típusa?"
		drawing="Csak_a_rajz"
		canvas="Rajzlap"
		exportof="Az exportált terület legyen: "
		Resolution="Felbontás (dpi)"
		Working="Készül a"
		Done="Az exportálás kész!" ;;
	esac

#################################################
#	PROGRAMME
######## Test dépendance ########
which inkscape 2>/dev/null
if [ $? != 0 ]
then
	zenity --error --title="$title" --text="$nobin"
	exit 0
fi

#### Pas de fichiers sélectionné ###
if [ $# -eq 0 ]; then
	zenity --error --title="$warning" --text="$noselec"
	exit 1
fi

######## Page/image ? ########
while [ ! "$choixutilisateur" ] # Réafficher la fenêtre tant que l'utilisateur n'a pas fait de choix
do
	choixutilisateur=`zenity --title "$title" --list --radiolist --column="" --column="$exportof" TRUE "$canvas" FALSE "$drawing" --text "$choix"`
	###### Choix -> Sortie boucle ######
	if  [ $? != 0 ]; then
		exit 1
	fi
	[ $? -ne 0 ] && exit 2 # Annulation
done

if  [ $choixutilisateur == $drawing ]; then
	type="--export-area-drawing";
fi

######## Résolution ? ########
while [ ! "$resolution" ] # Réafficher la fenêtre tant que l'utilisateur n'a pas fait de choix
do
######	resolution=`zenity --entry --title "$title" --text "$Resolution:" --entry-text "90"`
	resolution=`zenity --title="$title" --list --radiolist --column="" --column="$Resolution:" FALSE "90" FALSE "120" TRUE "300" FALSE "600" FALSE "1200"`
	###### Choix -> Sortie boucle ######
	if  [ $? != 0 ]; then
		exit 1
	fi
	[ $? -ne 0 ] && exit 2 # Annulation
done

######## Export png ########
while [ $# -gt 0 ]; do
	picture=$1
	png_file=`echo "$picture" | sed 's/\.\w*$/.png/'`
	inkscape $type --export-dpi="$resolution" --export-png="$png_file" "$picture" | zenity --progress --text="$Working $png_file" --pulsate --auto-close && zenity --info --text="$Done"
	shift
done
</code>
