---
author: kecsi
categories:
- linux
created: 1153304846
date: '2006-07-19T00:00:00Z'
excerpt: 'A minap megküzdöttem a jó öreg mutt levelzőprogramommal, mire be tudtam konfigurálni, hogy maildir formtumot tudjak vele olvasni. De sikerült, íime a konfiguráció: kecsi@rivendel:~$ cat .muttrc # # User configuration file for Mutt # set mbox_type=Maildir set folder="~/Maildir/" set spoolfile=~/Maildir/ set mask="!^\\.[^.]" set record="+.Sent" set postponed="+.Drafts" mailboxes `\ echo -n "+ "; \ for file in ~/Maildir/.*; do \ box=$(basename "$file"); \ if [ ! "$box" = ''.'' -a ! "$box" = ''..'' -a ! "$box" = ''.customflags'' \ -a ! "$box" = ''.subscriptions'' ]; then \'
title: Maildir olvasása mutt-tal
aliases:
- /node/179/
- /story/179/
---
A minap megküzdöttem a jó öreg mutt levelzőprogramommal, mire be tudtam konfigurálni, hogy maildir formtumot tudjak vele olvasni. De sikerült, íime a konfiguráció:

kecsi@rivendel:~$ cat .muttrc

<code>#
# User configuration file for Mutt
#
set mbox_type=Maildir
set folder="~/Maildir/"
set spoolfile=~/Maildir/
set mask="!^\\.[^.]"
set record="+.Sent"
set postponed="+.Drafts"
mailboxes `\
echo -n "+ "; \
for file in ~/Maildir/.*; do \
  box=$(basename "$file"); \
  if [ ! "$box" = '.' -a ! "$box" = '..' -a ! "$box" = '.customflags' \
       -a ! "$box" = '.subscriptions' ]; then \
    echo -n "+'$box' "; \
  fi; \
done`
</code>
<code>macro index c "<change-folder>?<toggle-mailboxes>" "open a different folder"
macro pager c "<change-folder>?<toggle-mailboxes>" "open a different folder"
</code>
<code>macro index C "<copy-message>?<toggle-mailboxes>" "copy a message to a mailbox"
macro index M "<save-message>?<toggle-mailboxes>" "move a message to a mailbox"
</code>
<cite>mbox_type</cite> és <cite>folder</cite> konfigurációs paraméter beállítása önmagában nem volt elég ahogy a <a href="http://www.elho.net/mutt/maildir/">fülest kaptam</a> `spoolfile` is kellett.
