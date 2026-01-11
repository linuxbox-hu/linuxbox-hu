---
layout: post
title: Thunderbird FileLink kiegészítés SeaFile-hoz
date: 2014-01-01
author: szimszon
categories: [linux]
tags: Seafile, Thunderbird
---
Nem régen írtam a [SeaFile](https://seafile.com)\-ról [itt](https://linuxbox.hu/node/860). Azóta közeledik a 2.1-es kiadása pár érdekes új képességgel mint a [WebDAV](https://webdav.org/).

Pár bacinak köszönhetően a doki ágynyugalmat írt elő. Így volt időm nézegetni a [Mozilla](https://www.mozilla.org/hu/) leírását a [FileLink](https://developer.mozilla.org/en-US/docs/Mozilla/Thunderbird/Filelink_Providers) api-ról, ami annyit tud, hogyha valaki [Thunderbird](https://www.mozilla.org/hu/thunderbird/)\-ben nagy fájlt akar küldeni annak lehetősége van rá, hogy egy felhő szolgáltatóhoz töltse fel a fájlt automatikusan és utána egy megosztási linket küldjön csak a levélben. Alapértelmezetten [DropBox](https://www.dropbox.com/), [YouSendIt](https://www.yousendit.com) és [UbuntuOne](https://one.ubuntu.com/) szolgáltatók érhetők el.

A [Mozilla](https://www.mozilla.org/hu/) referencia implementációja ([YouSendIt](http://mxr.mozilla.org/comm-central/source/mail/components/cloudfile/nsYouSendIt.js) szerencsére szinte egy az egyben megegyezik a [SeaFile](https://seafile.com) működési mechanizmusával. Így igazából csak az api hívásokat kellett kicserélni a [SeaFile](http://seafile.com) [api](https://github.com/haiwen/seafile/wiki/Seafile-web-API) hívásaira.

Így született meg az [első verzió](https://github.com/szimszon/tb-filelink-seafile/archive/master.zip) a kiterjesztésből. Mivel nem vagyok [Thunderbird](https://www.mozilla.org/hu/thunderbird/) kiterjesztés fejlesztő, sokkal többet nem tudok tenni a témában. Mindenki hozzájárulását szívesen fogadom, hogy minél jobb, szebb és használhatóbb legyen.

A kód elérhető a [GitHub](https://github.com/szimszon/tb-filelink-seafile)\-on.

Mindenkinek Boldog Új Évet és sok nagy fájlküldést :)
