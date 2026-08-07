# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Does

`linuxbox.hu` — a personal Hungarian-language Linux tips/tricks blog, built with Jekyll (`jekyll-theme-chirpy`), hosted on GitHub Pages. Content lives in `_posts/` as one markdown file per article, dating back to 2006.

## Working Conventions

- **Solo repo, no branches/PRs**: single maintainer. Commit and push directly to `main` — don't create feature branches or open PRs unless explicitly asked to.
- **Conventional Commits**: subject lines follow `type: description` (`post:`, `fix:`, `chore:` — see git log for examples).
- **Language**: posts are written in Hungarian, with proper diacritics (á é í ó ö ő ú ü ű). Note that many older posts predate this and are accent-free — that's historical, not a style to replicate in new content.
- **Post format**: short, practical, single-topic "trick" posts. Frontmatter: `layout: post`, `title`, `date`, `categories: [...]`, `tags: [...]`, optional `image:` (path under `assets/img/logos/`). Chirpy callout boxes (`{: .prompt-tip }`, `{: .prompt-info }`, `{: .prompt-warning }`) for asides. See `_posts/2026-08-08-etckeeper-etc-git-alatt.md` for a representative recent example (length, tone, structure).
- **Images**: third-party logos added under `assets/img/logos/` have historically carried no in-repo attribution note, even when their license (e.g. CC BY) technically calls for one — matches existing repo convention, not a recommendation to drop attribution research when sourcing new images.
- See `TODO.md` for planned work: article idea backlog and the bigger Hugo + multilingual (HU/EN) migration plan.
