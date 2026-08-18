---
author: kecsi
categories: []
created: 1230896181
date: '2009-01-02T00:00:00Z'
description: 'Fel lehet fogni poénnak is, de azt is el tudom képzelni hogy valaki ragaszkodik aa megszokotott c:\ -hez. :D export PS1=''C:${PWD//\//\\\}>'' A kódsor lecseréli a $PWD változóban (aktuális elérési út) linuxos /-t windowsos \-re így az eredmény: C:\home\ szerű prompt... Eredeti cikk.'
title: Windows-os parancssori prompt linux alatt :)
aliases:
- /blog/581/
- /node/581/
---
Fel lehet fogni poénnak is, de azt is el tudom képzelni hogy valaki ragaszkodik aa megszokotott c:\ -hez. :D
<code>
export PS1='C:${PWD//\//\\\}>'
</code>
A kódsor lecseréli a $PWD változóban (aktuális elérési út) linuxos /-t windowsos \-re így az eredmény: C:\home\ szerű prompt...

<a href="http://agafix.org/april-foul-windows-like-bash-prompt/">Eredeti cikk.</a>
