# TODO

Ismert hiányosságok, tervezett munkák a Chirpy Hugo-témára (`geekifan/hugo-theme-chirpy`) állás közben/után.

## i18n

- [x] ~~Magyar i18n fordítás a témához~~ - kész (2026-08-18). A téma valójában tartalmaz magyar fordítást
  (`_vendor/github.com/geekifan/hugo-theme-chirpy/i18n/hu-HU.yml`), csak a fájlnév/nyelvkulcs nem egyezett:
  Hugo a fordítási bundle-t a `languages.toml`-ban definiált nyelvkulcs (`hu`) alapján keresi, nem a
  `locale` mezőt nézi - így a `hu-HU.yml` sosem talált egyezést, és a lábléc/copyright szövegek üresen
  jelentek meg. Megoldás: `i18n/hu.yaml` hozzáadva helyi override-ként (a `hu-HU.yml` másolata).
- [ ] **PR upstream a `hu`/`hu-HU` fájlnév-eltérésről.** Érdemes jelezni a `geekifan/hugo-theme-chirpy`
  repónak, hogy a `hu-HU.yml` néven szállított fordítás gyakorlatban sosem illeszkedik semelyik `[hu]`
  nyelvkulcsú Hugo confighoz - vagy át kellene nevezni `hu.yaml`-ra, vagy dokumentálni kellene, hogy a
  `languages.toml`-ban `hu-HU`-t kell nyelvkulcsként használni, ha valaki ezt a fordítást szeretné.

- [ ] **`preview-img` bug PR upstream.** `layouts/index.html` és `layouts/post/single.html` is a
  `preview-img` classt közvetlenül az `<img>`-re teszi ahelyett, hogy egy körülötte lévő wrapper divre tenné -
  emiatt a kép torzul/nyúlik ahelyett, hogy a téma saját SCSS-e (`.preview-img { aspect-ratio: 40/21;
  overflow: hidden; img { object-fit: cover } }`) helyesen kivágná. Helyi javítás már megtörtént (lásd
  `layouts/index.html` és `layouts/post/single.html` ebben a repóban), csak az upstream PR van hátra.

## Egyéb ismert rések

- [x] ~~12 poszt több képpel (multi-image)~~ - kész (2026-08-18). Mind a 11 törött Drupal-képekre mutató
  poszt képe **visszaszerezhető** volt: a régi Drupal kódbázis és a feltöltött fájlok még megvannak a
  szerveren (`/var/www/linuxbox.hu/www.linuxbox.hu/web/sites/default/files/`). Mind a 36 egyedi kép
  letöltve és újrahosztolva a `static/assets/img/posts/` alá, a posztok markdown-ra konvertálva. 4 posztnak
  duplikált volt a teljes body-ja (migrációs hiba) - javítva. A 12. (backuppc) már eleve rendben volt.
- [ ] **~65 törött Drupal-kori képlink a teljes archívumban** - a fenti felfedezés alapján ez a többi eset is
  valószínűleg **visszaszerezhető ugyanígy** a szerveren lévő régi Drupal `sites/default/files` mappából,
  nem kell törölni/pótolni máshonnan. Meg kell nézni a teljes listát és ugyanígy végigmenni rajta.
- [ ] Config secretek (Mapbox/Algolia-stílusú kulcsok) még mindig üresek/kitöltetlenek a régi LoveIt configból
  átvéve - ellenőrizni, hogy az új Chirpy configban egyáltalán szükség van-e ezekre.
- [ ] `site.webmanifest` favicon fájl hiányzik (PWA jelenleg kikapcsolva, `site.Params.pwa.enabled` nincs
  beállítva, úgyhogy ez egyelőre nem probléma - de ha valaha PWA-t szeretnénk, ez is kelleni fog).
- [x] ~~`static/tools/run.sh` és `test.sh`~~ - törölve (2026-08-18). Ezek a régi Jekyll-es dev scriptek
  (`tools/run.sh`, `tools/test.sh`) tévedésből a `static/` alá kerültek a migráció során, így minden buildnél
  élesben is publikálódtak (`linuxbox.hu/tools/run.sh`, `/tools/test.sh`) - jekyll/html-proofer parancsokat
  hivatkozó, ma már irreleváns scriptek voltak kint nyilvánosan. Eltávolítva.
- [x] ~~`themes/LoveIt` git submodule eltávolítása~~ - kész (2026-08-18). A Chirpy-témára váltás előtti
  kísérlet maradványa volt, a téma ma már Hugo Modules-ön keresztül (`go.mod`, `geekifan/hugo-theme-chirpy`)
  töltődik be. `.gitmodules` és a `themes/LoveIt` submodule bejegyzés eltávolítva.
- [ ] **Automatikus deploy (GitHub Actions vagy hasonló) a jelenlegi kézi `git pull` + `hugo build`
  helyett.** Jelenleg minden éles frissítés kézi SSH-lépés a szerveren. Ide tartozik az is, hogy a build
  parancs használja a `--cleanDestinationDir` kapcsolót (2026-08-18: enélkül a `public/`-ból törölt/átnevezett
  fájlok - lásd a fenti `static/tools` esetet - némán bent maradnak a régi buildből, és tovább publikálódnak).
