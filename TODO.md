# TODO

Tervezett munkák, cikk ötletek, ismert hiányosságok.

## Big migrations

- [ ] **Hugo migráció + többnyelvűség (HU, EN)** — jelenleg Jekyll (`jekyll-theme-chirpy`), egynyelvű (`lang: hu-HU` a `_config.yml`-ben). Cél: átállás Hugóra, és a tartalom kétnyelvűvé tétele (magyar + angol). Nagyobb, több lépéses munka:
  1. Hugo-kompatibilis téma kiválasztása (Chirpy-hez hasonló stílusban, pl. [hugo-PaperMod](https://github.com/adityatelange/hugo-PaperMod) vagy [hugo-chirpy](https://github.com/anlutro/hugo-chirpy) jellegű) — vizuális stílus/kategóriák/tag-ek megtartása legyen szempont
  2. Meglévő `_posts/*.md` frontmatter konverzió Jekyll → Hugo formátumra (`categories`/`tags`/`date`/`image` mezők átalakítása, `layout: post`/`layout: story` megszüntetése, Hugo content type- okra váltás)
  3. URL-struktúra megtartása vagy redirect terv (SEO, meglévő linkek ne törjenek — sok bejövő link mutat régi node-okra is, l. `https://linuxbox.hu/node/XXX` hivatkozások a régebbi posztokban)
  4. Többnyelvűség bevezetése Hugo natív i18n-jével (`content/hu/`, `content/en/` vagy `.hu.md`/`.en.md` fájl suffix minta) — eldönteni: minden régi poszt kapjon angol fordítást, vagy csak az újak mostantól legyenek HU+EN, régiek maradjanak HU-only
  5. GitHub Pages / Actions build pipeline átírása Jekyll build lépésről Hugo buildre (`.github/workflows/`)
  6. `_data/locales` és egyéb Chirpy-specifikus lokalizációs fájlok Hugo i18n megfelelőjére cserélése

## Cikk ötletek

Kisebb, önmagában megálló Linux tippek/trükkök korábbi homelab munkából — rövid, egy-egy témás poszt formátumban (l. `_posts/2026-08-08-etckeeper-etc-git-alatt.md` mint minta a hosszra/stílusra).

- [x] **etckeeper** — `/etc` könyvtár git alatt automatikus verziókövetéssel — megjelent 2026-08-08 (`_posts/2026-08-08-etckeeper-etc-git-alatt.md`)
- [ ] **Midnight Commander + gruvbox skin** — gyors nosztalgia/QoL poszt, egy URL, egy parancs a szép MC témához
- [ ] **chrony vs ntpd** — Debian 13 (Trixie) kivezette az `ntp` csomagot; rövid "ha Trixie-n vagy, válts chrony-ra" poszt, esetleg + MikroTik router mint NTP forrás (kapcsolódik a meglévő RouterOS poszthoz)
- [ ] **Friss gép biztonsági alapcsomagja 5 perc alatt** — fail2ban + rkhunter + lynis 3 apt paranccsal, "hardening checklist" jelleggel
- [ ] **LVM: fájlrendszer bővítése élesben, leállás nélkül** — `lvextend` + `resize2fs`, konkrét, gyakorlati sysadmin trükk
- [ ] **systemd graceful shutdown / grace period-ok** — miért ne csak kihúzzuk a gépet; hogyan működik a systemd leállási sorrend és timeout, általánosítva túl a Kubernetes-specifikus eseten
- [ ] **SSH kulcsok jelszókezelőből/vault-ból, ne plaintext-ben** — általános "ne hardcode-old az SSH kulcsaidat" minta (infra-specifikus rész nélkül, csak az elv)
- [ ] **Bash/WSL2 shell feldobása** — fzf + oh-my-posh + bash aliasok összefoglaló poszt, nulla infra tartalommal, jól megosztható
- [ ] **WSL2 buktatók** — `systemd = true`, hálózati mód, port bind furcsaságok; konkrét "miért nem működik ez" hibakeresési történetek, önálló posztokként is működhetnek
- [ ] **Firefox HSTS cache reset trükk** — `SiteSecurityServiceState.bin` törlése, amikor egy réginek hitt tanúsítvány miatt beragad a böngésző
- [ ] **MikroTik RouterOS trükkök sorozat** — a meglévő DNS adlist poszt folytatásaként: statikus DNS bejegyzések API-n keresztül, NAT port-forward automatizálás, router mint NTP szerver
