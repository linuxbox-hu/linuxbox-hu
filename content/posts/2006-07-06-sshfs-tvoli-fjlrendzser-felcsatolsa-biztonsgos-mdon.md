---
author: kecsi
categories:
- debian
created: 1152200214
date: '2006-07-06T00:00:00Z'
excerpt: |
  A már ismert <a href="http://fuse.sourceforge.net/">fuse</a> kernel modullal fel tudunk csatolni távoli fájlrendszereket az sshd démont használva <a href="http://fuse.sourceforge.net/sshfs.html">sshfs</a> ségítségével.
  1. Pl. debian rendszeren a szoftver telepítése:
  <code> apt-get install sshfs</code>
  2. Majd ellenőrizzük be van-e töltve a fuse kernel modul:
  <code>modprobe fuse</code>
  3. Adjuk be felhasználónk a fuse csoportba:
  <code>usermod -G fuse felhasznalo</code>
  4. Majd neki is eshetünk használni a dolgot:
  <code>mkdir ~/remote_folder
  sshfs user1@remote_server:/tmp ~/remote_folder</code>
title: 'sshfs - távoli fájlrendzser felcsatolása biztonságos módon'
---
A már ismert <a href="http://fuse.sourceforge.net/">fuse</a> kernel modullal fel tudunk csatolni távoli fájlrendszereket az sshd démont használva <a href="http://fuse.sourceforge.net/sshfs.html">sshfs</a> ségítségével.
1. Pl. debian rendszeren a szoftver telepítése:
<code> apt-get install sshfs</code>
2. Majd ellenőrizzük be van-e töltve a fuse kernel modul:
<code>modprobe fuse</code>
3. Adjuk be felhasználónk a fuse csoportba:
<code>usermod -G fuse felhasznalo</code>
4. Majd neki is eshetünk használni a dolgot:
<code>mkdir ~/remote_folder
sshfs user1@remote_server:/tmp ~/remote_folder</code>
<!--break-->
5. Dolgunk végeztével így csatolhatjuk le:
<code>fusermount -u ~/remote_folder</code>

/etc/fstabbal meg is könnyíthetjük ezt a procedurát:
<code>sshfs#user1@remote_server:/tmp /home/user1/remote_folder/ fuse defaults,auto 0 0</code>
