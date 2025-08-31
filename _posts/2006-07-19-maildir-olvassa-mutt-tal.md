---
excerpt: "A minap megküzdöttem a jó öreg mutt levelzőprogramommal, mire be tudtam
  konfigurálni, hogy maildir formtumot tudjak vele olvasni. De sikerült, íime a konfiguráció:\r\n\r\nkecsi@rivendel:~$
  cat .muttrc\r\n\r\n<code>#\r\n# User configuration file for Mutt\r\n#\r\nset mbox_type=Maildir\r\nset
  folder=\"~/Maildir/\"\r\nset spoolfile=~/Maildir/\r\nset mask=\"!^\\\\.[^.]\"\r\nset
  record=\"+.Sent\"\r\nset postponed=\"+.Drafts\"\r\nmailboxes `\\\r\necho -n \"+
  \"; \\\r\nfor file in ~/Maildir/.*; do \\\r\n  box=$(basename \"$file\"); \\\r\n
  \ if [ ! \"$box\" = '.' -a ! \"$box\" = '..' -a ! \"$box\" = '.customflags' \\\r\n
  \      -a ! \"$box\" = '.subscriptions' ]; then \\\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: Maildir olvasása mutt-tal
created: 1153304846
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
<cite>mbox_type</cite> és <cite>folder</cite> konfigurációs paraméter beállítása önmagában nem volt elég ahogy a <a href="http://www.elho.net/mutt/maildir/">fülest kaptam</a> <strong>spoolfile</strong> is kellett.
