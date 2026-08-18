---
author: kecsi
categories:
- linux
created: 1146247811
date: '2006-04-28T00:00:00Z'
excerpt: |-
  Ha egy távoli gépre például jelszó nélkül akarsz bejutni ssh-val, akkor használhatsz ssh kulcsokat.
  Ennek a beállítása mindössze pár utasítás:
  1. Generálj egy SSH kulcsot magadnak ehhez a művelethez.
  <code>ssh-keygen -t dsa</code>
  Ne adj meg jelszót amikor jelszavas védelmet akar tenni a kulcsra.
  2. Másold át a publikus kulcsát a frissen generált kulcspárodnak(publikus és privát).
  <code>scp ~/.ssh/id_dsa.pub masikgep.teljes.neve:.ssh/authorized_keys2</code>
  Ezután már próbálhasz is átlépnizni jelszó nélkül.
  <code>ssh masikgep.teljes.neve</code>
title: SSH kulcsok használata
aliases:
- /node/148/
- /story/148/
---
Ha egy távoli gépre például jelszó nélkül akarsz bejutni ssh-val, akkor használhatsz ssh kulcsokat.
Ennek a beállítása mindössze pár utasítás:
1. Generálj egy SSH kulcsot magadnak ehhez a művelethez.
<code>ssh-keygen -t dsa</code>
Ne adj meg jelszót amikor jelszavas védelmet akar tenni a kulcsra.
2. Másold át a publikus kulcsát a frissen generált kulcspárodnak(publikus és privát).
<code>scp ~/.ssh/id_dsa.pub masikgep.teljes.neve:.ssh/authorized_keys2</code>
Ezután már próbálhasz is átlépnizni jelszó nélkül.
<code>ssh masikgep.teljes.neve</code>
