---
excerpt: "SMTP szerver konfugurálás közben jól jön, ha telnettel tudunk mailszervert
  tesztelni.\r\nÍme egy példa:\r\n<code>\r\n$ telnet smtp.pelda.hu smtp\r\nTrying
  192.0.34.72...\r\nConnected to smtp.example.com.\r\nEscape character is '^]'.\r\n220
  smtp.pelda.hu ESMTP Postfix (Debian/GNU)\r\nHELO smtp.vhol.hu\r\n250 smtp.example.com\r\nMAIL
  From: kecsi@nemtomDEnemletezik.hu\r\n250 Ok\r\nRCPT To: haver@valaholDEnemletezik.hu\r"
categories:
- linux
layout: story
author: kecsi
title: SMTP teszt telnettel
created: 1140259972
---
SMTP szerver konfugurálás közben jól jön, ha telnettel tudunk mailszervert tesztelni.
Íme egy példa:
<code>
$ telnet smtp.pelda.hu smtp
Trying 192.0.34.72...
Connected to smtp.example.com.
Escape character is '^]'.
220 smtp.pelda.hu ESMTP Postfix (Debian/GNU)
HELO smtp.vhol.hu
250 smtp.example.com
MAIL From: kecsi@nemtomDEnemletezik.hu
250 Ok
RCPT To: haver@valaholDEnemletezik.hu
250 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
Hello!
Kene nekem egykis linux segitseg.
.
250 Ok: queued as F169C23068
QUIT
221 Bye
Connection closed by foreign host. 
</code>
A levél végét a szöveg utolsó sorában a <strong>.</strong> adja!
