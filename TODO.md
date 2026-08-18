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
- [x] ~~Small-hero opt-in for logo-style front-matter images~~ - done (2026-08-18). `2015-02-03-backuppc`,
  `2026-02-15-routeros-dns-adlist`, `2026-08-08-etckeeper-etc-git-alatt` had their front-matter `image:` +
  duplicate inline body image deduped first, but the post-page hero still rendered at the site-wide
  `.preview-img` size (full-width, 40/21 aspect ratio) - too big for a small square/wide logo (vs. a real
  photo). Added an opt-in `image.small: true` front-matter flag, read in `layouts/post/single.html`, that
  caps the hero to `max-width: 30%` only on posts that set it; the homepage card (`layouts/index.html`) and
  every other post's default full-width banner (e.g. `welcome-to-jekyll`) are untouched.

## Other known gaps

- [x] ~~12 multi-image posts~~ - done (2026-08-18). All 11 posts pointing at broken Drupal images turned
  out to be **recoverable**: the old Drupal codebase and uploads are still intact on the server
  (`/var/www/linuxbox.hu/www.linuxbox.hu/web/sites/default/files/`). All 36 individual images downloaded
  and rehosted under `static/assets/img/posts/`, posts converted to Markdown. 4 posts had their whole body
  duplicated (a migration bug) - fixed. The 12th post (backuppc) was already fine.
- [x] ~~~65 broken Drupal-era image links across the whole archive~~ - done (2026-08-18). Found 83 dead
  `/sites/default/files/*` references across 30 posts (plus one `.txt` attachment link), all recoverable
  the same way from the old Drupal files on the server. All 84 files fetched and rehosted under
  `static/assets/img/posts/` (images) and `static/assets/files/posts/` (the one text attachment), all 30
  posts rewritten to clean Markdown with fixed paths.
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
- [x] ~~Automatic deploy (GitHub Actions or similar) instead of the current manual `git pull` + `hugo
  build`~~ - done (2026-08-18). `.github/workflows/deploy.yml` added: SSHes into the server as a dedicated
  unprivileged deploy user (own OS user, no sudo) and runs
  `git fetch <public HTTPS URL> main && git reset --hard FETCH_HEAD` (an explicit URL, not touching the
  checkout's own `origin` remote, so manual pushes/pulls from the same checkout keep working over SSH
  untouched) then `hugo --gc --minify --cleanDestinationDir`, then explicit `chmod 755`/`644` on `public/` -
  this makes the build output world-readable directly, sidestepping the `www-data` group-membership approach
  entirely for future deploys. Server-side account/access setup was done out of band, not tracked here.

## Article ideas

Carried over from the old Jekyll repo's TODO.md (2026-08-18) - small, self-contained Linux tips/tricks from
earlier homelab work, one topic per short post (see `2026-08-08-etckeeper-etc-git-alatt.md` for the
length/style baseline).

- [x] ~~etckeeper~~ - `/etc` under git with automatic version tracking - published 2026-08-08
  (`2026-08-08-etckeeper-etc-git-alatt.md`)
- [ ] **Midnight Commander + gruvbox skin** - quick nostalgia/QoL post, one URL and one command for the nice
  MC theme
- [ ] **chrony vs ntpd** - Debian 13 (Trixie) dropped the `ntp` package; short "if you're on Trixie, switch to
  chrony" post, maybe plus a MikroTik router as an NTP source (ties into the existing RouterOS post)
- [ ] **A fresh box's basic security kit in 5 minutes** - fail2ban + rkhunter + lynis via 3 apt commands, as a
  "hardening checklist"
- [ ] **LVM: extending a filesystem live, no downtime** - `lvextend` + `resize2fs`, a concrete, practical
  sysadmin trick
- [ ] **systemd graceful shutdown / grace periods** - why not just pull the plug; how systemd's shutdown
  ordering and timeouts actually work, generalized beyond the Kubernetes-specific case
- [ ] **SSH keys from a password manager/vault, not plaintext** - the general "don't hardcode your SSH keys"
  pattern (no infra-specific part, just the principle)
- [ ] **Sprucing up the Bash/WSL2 shell** - fzf + oh-my-posh + bash aliases roundup post, zero infra content,
  easy to share
- [ ] **WSL2 gotchas** - `systemd = true`, networking mode, port-bind oddities; concrete "why doesn't this
  work" debugging stories, could work as standalone posts too
- [ ] **Firefox HSTS cache reset trick** - deleting `SiteSecurityServiceState.bin` when the browser gets stuck
  on a certificate it thinks is stale
- [ ] **MikroTik RouterOS tricks series** - continuing the existing DNS adlist post: static DNS entries via
  the API, NAT port-forward automation, router as an NTP server
