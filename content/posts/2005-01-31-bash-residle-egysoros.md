---
author: kecsi
categories:
- linux
created: 1107211604
date: '2005-01-31T00:00:00Z'
title: Bash üres(idle) egysoros
aliases:
- /node/3/
- /story/3/
---
<strong>while (echo '') do w; sleep 60; done</strong>

Ez a pici kód percenként egy üres sort ir ki a terminálodban. Így pl. meg tudod tartani a kapcsolatod akkor is a távoli géppel, ha azon idled működik.
