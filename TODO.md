# TODO

Known gaps and planned work around the switch to the Chirpy Hugo theme (`geekifan/hugo-theme-chirpy`).

## i18n

- [x] ~~Hungarian i18n translation for the theme~~ - done (2026-08-18). The theme actually ships a
  Hungarian translation (`_vendor/github.com/geekifan/hugo-theme-chirpy/i18n/hu-HU.yml`), it just never
  matched: Hugo resolves the i18n bundle by the language key defined in `languages.toml` (`hu`), not by the
  `locale` field - so `hu-HU.yml` never matched, and footer/copyright strings rendered blank. Fixed by
  adding `i18n/hu.yaml` as a local override (a copy of `hu-HU.yml`).
- [ ] **Upstream PR about the `hu`/`hu-HU` filename mismatch.** Worth flagging to
  `geekifan/hugo-theme-chirpy` that the translation shipped as `hu-HU.yml` never actually matches any Hugo
  config using `[hu]` as the language key in practice - either rename it to `hu.yaml`, or document that
  `languages.toml` needs to use `hu-HU` as the language key to pick up this translation.

- [ ] **`preview-img` bug PR upstream.** Both `layouts/index.html` and `layouts/post/single.html` put the
  `preview-img` class directly on the `<img>` instead of on a wrapper div around it - this distorts/stretches
  the image instead of letting the theme's own SCSS (`.preview-img { aspect-ratio: 40/21; overflow: hidden;
  img { object-fit: cover } }`) crop it correctly. Local fix already done (see `layouts/index.html` and
  `layouts/post/single.html` in this repo), only the upstream PR is outstanding.

## Other known gaps

- [x] ~~12 multi-image posts~~ - done (2026-08-18). All 11 posts pointing at broken Drupal images turned
  out to be **recoverable**: the old Drupal codebase and uploads are still intact on the server
  (`/var/www/linuxbox.hu/www.linuxbox.hu/web/sites/default/files/`). All 36 individual images downloaded
  and rehosted under `static/assets/img/posts/`, posts converted to Markdown. 4 posts had their whole body
  duplicated (a migration bug) - fixed. The 12th post (backuppc) was already fine.
- [ ] **~65 broken Drupal-era image links across the whole archive** - based on the discovery above, these
  are likely **recoverable the same way** from the old Drupal `sites/default/files` folder on the server,
  no need to delete/replace from elsewhere. Need to go through the full list and work through it the same way.
- [ ] Config secrets (Mapbox/Algolia-style keys) are still empty/unfilled, carried over from the old LoveIt
  config - check whether the new Chirpy config even needs these at all.
- [ ] `site.webmanifest` favicon file is missing (PWA is currently disabled, `site.Params.pwa.enabled` isn't
  set, so this isn't an issue for now - but it'll be needed if we ever want PWA support).
- [x] ~~`static/tools/run.sh` and `test.sh`~~ - removed (2026-08-18). These old Jekyll-era dev scripts
  (`tools/run.sh`, `tools/test.sh`) ended up under `static/` by mistake during the migration, so they were
  being published live on every build (`linuxbox.hu/tools/run.sh`, `/tools/test.sh`) - scripts referencing
  jekyll/html-proofer that are now irrelevant, sitting out there publicly. Removed.
- [x] ~~Remove the `themes/LoveIt` git submodule~~ - done (2026-08-18). Leftover from before the switch to
  Chirpy; the theme now loads via Hugo Modules (`go.mod`, `geekifan/hugo-theme-chirpy`). `.gitmodules` and
  the `themes/LoveIt` submodule entry removed.
- [ ] **Automatic deploy (GitHub Actions or similar) instead of the current manual `git pull` + `hugo
  build`.** Right now every production update is a manual SSH step on the server. This should also make the
  build command use `--cleanDestinationDir` (2026-08-18: without it, files removed/renamed out of `public/`
  - see the `static/tools` case above - silently stick around from the previous build and keep being served).
