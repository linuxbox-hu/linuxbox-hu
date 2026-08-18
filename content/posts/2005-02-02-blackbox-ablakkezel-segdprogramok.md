---
author: kecsi
categories:
- x
created: 1107350140
date: '2005-02-02T00:00:00Z'
excerpt: 'A blackbox egy rendkívül gyors ablakkezelő. Sajnos emiatt kevés alapszolgáltatást nyújt. De ezen lehet javítani pl. úgy ha néhány segéd alakalmazást használunk vele együtt! bbkeys -i& bbpager& rm -f /home/kecsi/.lineak/lineakd.pid& lineakd& xscreensaver -lock-mode -no-splash -timeout 15& gkrellm -g +1200+8& root-tail -g 210x75+6+0 -f /var/log/all.log& blackbox Egykis mi-micsoda: bbkeys - blackbox gyorsbillentyű kezelő bbpager - blackbox virtualis desktop kezelő lineakd - inernetes billentyű extra gombokat kezelő démon gkrellm - valós idejű diag progi'
title: blackbox ablakkezelő segédprogramok
aliases:
- /node/15/
- /story/15/
---
A blackbox egy rendkívül gyors ablakkezelő. Sajnos emiatt kevés alapszolgáltatást nyújt. De ezen lehet javítani pl. úgy ha   néhány segéd alakalmazást használunk vele együtt!
```bash
bbkeys -i&
bbpager&
rm -f /home/kecsi/.lineak/lineakd.pid&
lineakd&
xscreensaver -lock-mode -no-splash -timeout 15&
gkrellm -g +1200+8&
root-tail -g 210x75+6+0 -f /var/log/all.log&
blackbox
```
Egykis mi-micsoda:
bbkeys - blackbox gyorsbillentyű kezelő
bbpager - blackbox virtualis desktop kezelő
lineakd - inernetes billentyű extra gombokat kezelő démon
gkrellm - valós idejű diag progi
root-tail - X desktopon log megjelenitő
