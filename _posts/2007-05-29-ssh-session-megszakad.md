---
excerpt: Ha egy tűzfal mögötti, NAT-olt hálózatról ssh terminálban hosszasan időzve
  megszakad a kapcsolatunk a távoli ssh szerverrel akkor érdemes kliens oldalon a
  <code>/etc/ssh/ssh_config </code> állományban beállítani a <code>ServerAliveInterval
  60</code> változót. Így megszüntetve a folytonos újrakapcsolódás kellemetlenségeit.
categories:
- linux
layout: story
author: kecsi
title: Ssh session megszakad?
created: 1180444921
---
Ha egy tűzfal mögötti, NAT-olt hálózatról ssh terminálban hosszasan időzve megszakad a kapcsolatunk a távoli ssh szerverrel akkor érdemes kliens oldalon a <code>/etc/ssh/ssh_config </code> állományban beállítani a <code>ServerAliveInterval 60</code> változót. Így megszüntetve a folytonos újrakapcsolódás kellemetlenségeit.
