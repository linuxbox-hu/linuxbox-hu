---
author: kecsi
categories:
- linux
created: 1180444921
date: '2007-05-29T00:00:00Z'
description: Ha egy tűzfal mögötti, NAT-olt hálózatról ssh terminálban hosszasan időzve megszakad a kapcsolatunk a távoli ssh szerverrel akkor érdemes kliens oldalon a /etc/ssh/ssh_config állományban beállítani a ServerAliveInterval 60 változót. Így megszüntetve a folytonos újrakapcsolódás kellemetlenségeit.
title: Ssh session megszakad?
aliases:
- /node/379/
- /story/379/
---
Ha egy tűzfal mögötti, NAT-olt hálózatról ssh terminálban hosszasan időzve megszakad a kapcsolatunk a távoli ssh szerverrel akkor érdemes kliens oldalon a <code>/etc/ssh/ssh_config </code> állományban beállítani a <code>ServerAliveInterval 60</code> változót. Így megszüntetve a folytonos újrakapcsolódás kellemetlenségeit.
