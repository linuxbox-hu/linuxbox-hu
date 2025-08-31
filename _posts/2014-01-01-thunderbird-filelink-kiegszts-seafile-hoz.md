---
excerpt: "<p>Nem régen írtam a <a title=\"http://seafile.com\" target=\"_blank\" href=\"http://seafile.com\">SeaFile</a>-ról
  <a title=\"https://linuxbox.hu/node/860\" target=\"_blank\" href=\"https://linuxbox.hu/node/860\">itt</a>.
  Azóta közeledik a 2.1-es kiadása pár érdekes új képességgel mint a <a title=\"http://webdav.org/\"
  target=\"_blank\" href=\"http://webdav.org/\">WebDAV</a>.\r\n</p>"
categories:
- hírek
layout: story
author: szimszon
mail: szimszon@oregpreshaz.eu
title: Thunderbird FileLink kiegészítés SeaFile-hoz
created: 1388603977
---
<p>Nem régen írtam a <a title="http://seafile.com" target="_blank" href="http://seafile.com">SeaFile</a>-ról <a title="https://linuxbox.hu/node/860" target="_blank" href="https://linuxbox.hu/node/860">itt</a>. Azóta közeledik a 2.1-es kiadása pár érdekes új képességgel mint a <a title="http://webdav.org/" target="_blank" href="http://webdav.org/">WebDAV</a>.
</p>
<p>Pár bacinak köszönhetően a doki ágynyugalmat írt elő. Így volt időm nézegetni a <a title="http://www.mozilla.org/hu/" target="_blank" href="http://www.mozilla.org/hu/">Mozilla</a> leírását a <a title="https://developer.mozilla.org/en-US/docs/Mozilla/Thunderbird/Filelink_Providers" target="_blank" href="https://developer.mozilla.org/en-US/docs/Mozilla/Thunderbird/Filelink_Providers">FileLink</a> api-ról, ami annyit tud, hogyha valaki <a title="https://www.mozilla.org/hu/thunderbird/" target="_blank" href="https://www.mozilla.org/hu/thunderbird/">Thunderbird</a>-ben nagy fájlt akar küldeni annak lehetősége van rá, hogy egy felhő szolgáltatóhoz töltse fel a fájlt automatikusan és utána egy megosztási linket küldjön csak a levélben. Alapértelmezetten <a title="https://www.dropbox.com/" target="_blank" href="https://www.dropbox.com/">DropBox</a>, <a title="https://www.yousendit.com" target="_blank" href="https://www.yousendit.com">YouSendIt</a> és <a title="https://one.ubuntu.com/" target="_blank" href="https://one.ubuntu.com/">UbuntuOne</a> szolgáltatók érhetők el.
</p>
<p>A <a title="http://www.mozilla.org/hu/" target="_blank" href="http://www.mozilla.org/hu/">Mozilla</a> referencia implementációja (<a title="http://mxr.mozilla.org/comm-central/source/mail/components/cloudfile/nsYouSendIt.js" target="_blank" href="http://mxr.mozilla.org/comm-central/source/mail/components/cloudfile/nsYouSendIt.js">YouSendIt</a>) szerencsére szinte egy az egyben megegyezik a <a title="http://seafile.com" target="_blank" href="http://seafile.com">SeaFile</a> működési mechanizmusával. Így igazából csak az api hívásokat kellett kicserélni a <a title="http://seafile.com" target="_blank" href="http://seafile.com">SeaFile</a> <a title="https://github.com/haiwen/seafile/wiki/Seafile-web-API" target="_blank" href="https://github.com/haiwen/seafile/wiki/Seafile-web-API">api</a> hívásaira.
</p>
<p>Így született meg az <a title="https://github.com/szimszon/tb-filelink-seafile/archive/master.zip" target="_blank" href="https://github.com/szimszon/tb-filelink-seafile/archive/master.zip">első verzió</a> a kiterjesztésből. Mivel nem vagyok <a title="https://www.mozilla.org/hu/thunderbird/" target="_blank" href="https://www.mozilla.org/hu/thunderbird/">Thunderbird</a> kiterjesztés fejlesztő, sokkal többet nem tudok tenni a témában. Mindenki hozzájárulását szívesen fogadom, hogy minél jobb, szebb és használhatóbb legyen.
</p>
<p>A kód elérhető a <a title="https://github.com/szimszon/tb-filelink-seafile" target="_blank" href="https://github.com/szimszon/tb-filelink-seafile">GitHub</a>-on.
</p>
<p>Mindenkinek Boldog Új Évet és sok nagy fájlküldést :)
  <br />
</p>
