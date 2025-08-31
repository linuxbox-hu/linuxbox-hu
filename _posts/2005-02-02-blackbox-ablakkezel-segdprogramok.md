---
excerpt: "A blackbox egy rendkívül gyors ablakkezelő. Sajnos emiatt kevés alapszolgáltatást
  nyújt. De ezen lehet javítani pl. úgy ha   néhány segéd alakalmazást használunk
  vele együtt!\r\n<strong>\r\nbbkeys -i&\r\nbbpager&\r\nrm -f /home/kecsi/.lineak/lineakd.pid&\r\nlineakd&\r\nxscreensaver
  -lock-mode -no-splash -timeout 15&\r\ngkrellm -g +1200+8&\r\nroot-tail -g 210x75+6+0
  -f /var/log/all.log&\r\nblackbox\r\n</strong>\r\nEgykis mi-micsoda:\r\nbbkeys -
  blackbox gyorsbillentyű kezelő\r\nbbpager - blackbox virtualis desktop kezelő\r\nlineakd
  - inernetes billentyű extra gombokat kezelő démon\r\ngkrellm - valós idejű diag
  progi\r"
categories:
- x
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: blackbox ablakkezelő segédprogramok
created: 1107350140
---
A blackbox egy rendkívül gyors ablakkezelő. Sajnos emiatt kevés alapszolgáltatást nyújt. De ezen lehet javítani pl. úgy ha   néhány segéd alakalmazást használunk vele együtt!
<strong>
bbkeys -i&
bbpager&
rm -f /home/kecsi/.lineak/lineakd.pid&
lineakd&
xscreensaver -lock-mode -no-splash -timeout 15&
gkrellm -g +1200+8&
root-tail -g 210x75+6+0 -f /var/log/all.log&
blackbox
</strong>
Egykis mi-micsoda:
bbkeys - blackbox gyorsbillentyű kezelő
bbpager - blackbox virtualis desktop kezelő
lineakd - inernetes billentyű extra gombokat kezelő démon
gkrellm - valós idejű diag progi
root-tail - X desktopon log megjelenitő
