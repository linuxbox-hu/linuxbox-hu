# TODO

Ismert hiányosságok, tervezett munkák a Chirpy Hugo-témára (`geekifan/hugo-theme-chirpy`) állás közben/után.

## i18n

- [ ] **Magyar i18n fordítás a témához, és PR upstream.** A téma jelenleg csak `fa-IR.yaml`-t tartalmaz
  (`_vendor/github.com/geekifan/hugo-theme-chirpy/i18n/`) - nincs `hu.yaml`, így az olyan UI szövegek mint
  "Posted on"/"Updated on"/"Written by"/pagination stb. angolul jelennek meg a magyar oldalon is, a
  `languages.hu.locale = "hu"` beállítás ellenére. A Jekyll-es Chirpy saját `hu-HU.yml` fordítása
  (`_data/locales/hu-HU.yml` a `jekyll-theme-chirpy` gemben) jó kiindulópont/referencia a kulcsokhoz és a
  fordításokhoz. Cél: `i18n/hu.yaml` elkészítése ebben a repóban (helyi override, a téma saját i18n mappájával
  megegyező struktúrában), majd PR-ban felajánlani a `geekifan/hugo-theme-chirpy` upstream repónak is.

## Egyéb ismert rések

- [ ] 12 poszt több képpel (multi-image) - ki lettek hagyva a kép front-matter promócióból, egyelőre a
  body-ban maradnak inline képek formájában.
- [ ] ~65 törött Drupal-kori képlink (`/sites/default/files/...`) a régi archívumban - a téma-váltástól
  független, előbb-utóbb érdemes lenne egyenként pótolni vagy törölni.
- [ ] Config secretek (Mapbox/Algolia-stílusú kulcsok) még mindig üresek/kitöltetlenek a régi LoveIt configból
  átvéve - ellenőrizni, hogy az új Chirpy configban egyáltalán szükség van-e ezekre.
- [ ] `site.webmanifest` favicon fájl hiányzik (PWA jelenleg kikapcsolva, `site.Params.pwa.enabled` nincs
  beállítva, úgyhogy ez egyelőre nem probléma - de ha valaha PWA-t szeretnénk, ez is kelleni fog).
