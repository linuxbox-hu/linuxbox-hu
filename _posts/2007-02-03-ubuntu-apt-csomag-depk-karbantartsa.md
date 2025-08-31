---
excerpt: "Gondolom nem én vagyok az egyetlen aki nem szereti a rendetlenséget. :D
  Az utóbbi időben már nem volt átlátható az /etc/apt/sources.list állományom. Nemrég
  belefutottam a  /etc/apt/sources.list.d/ könyvtár használatának lehetőségébe és
  elkezdtem rendet teremteni...\r\n\r\nAz eredmény tetszetős:\r\n<code>\r\n[6.][kecsi@otthonimasina]:/etc/apt>
  \ ls -1 sources.list.d/\r\n3v1deb.list\r\nberyl.list\r\nbmpx.list\r\ncompiz.list\r\ndebubuntu.list\r\ngoogle.list\r\nmedibuntu.list\r\nopera.list\r\nskype.list\r\nsubpixel.list\r\n</code>\r\n\r"
categories:
- ubuntu
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Ubuntu apt csomag depók karbantartása
created: 1170488867
---
Gondolom nem én vagyok az egyetlen aki nem szereti a rendetlenséget. :D Az utóbbi időben már nem volt átlátható az /etc/apt/sources.list állományom. Nemrég belefutottam a  /etc/apt/sources.list.d/ könyvtár használatának lehetőségébe és elkezdtem rendet teremteni...

Az eredmény tetszetős:
<code>
[6.][kecsi@otthonimasina]:/etc/apt>  ls -1 sources.list.d/
3v1deb.list
beryl.list
bmpx.list
compiz.list
debubuntu.list
google.list
medibuntu.list
opera.list
skype.list
subpixel.list
</code>

Én még Ubuntu Edgy-t használok, ha kíváncsi vagy az <a href="/filebrowser/ubuntu-apt">állományok tartalmára a bőngészőben megkuksizhatod</a> őket. Persze a gpg kulcsokat még majd be kell gyűjteni a depók használatához!

Mindenkinek tudom ajánlani, hogy külön tartsa az egyes repók elérhetőségét. Kellemesebb az élet így :)
