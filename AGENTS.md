# browser-userscripts — AGENTS.md

**Generated:** 2026-10-09
**Commit:** 0d71bd4
**Branch:** main

## OVERVIEW

Monorepo for Tampermonkey userscripts + DevTools console snippets. Live script: TimerHooker Ultimate (timer/video+audio speed, GPL-3.0-or-later).

## STRUCTURE

```text
browser-userscripts/
├── tampermonkey/timerhooker-ultimate/  # release .user.js + verbatim carcass + README + CHANGELOG
├── tampermonkey/_template/             # empty — future new-script skeleton
├── console/                            # devtools snippets, NOT userscripts (placeholder.js only)
├── README.md / LICENSE / .gitignore
```

## WHERE TO LOOK

| Task | Location | Notes |
|---|---|---|
| Release userscript | `tampermonkey/timerhooker-ultimate/timerhooker-ultimate.user.js` | v2.0.0, only file GreasyFork syncs |
| Verbatim reference | `tampermonkey/timerhooker-ultimate/2026-carcass.user.js` | 2026 base 1.4.2, read-only, never edit |
| Script docs | `tampermonkey/timerhooker-ultimate/README.md`, `CHANGELOG.md`, `greasyfork-description.md` + `greasyfork-description.html` | README usage/shortcuts table = content source; `greasyfork-description.*` are the verbatim GreasyFork Admin-tab sync sources |
| Repo docs | `README.md` | Script table + GreasyFork link |
| Snippets | `console/` | One file per snippet + README entry |
| Reference inputs (outside repo) | `D:\Temp\` | comparison reports, TSun sources — never move into repo |

## CONVENTIONS

- One folder per script: `<slug>/<slug>.user.js` + `README.md` + `CHANGELOG.md`.
- Userscript header (every release file): `@name`, `@namespace https://github.com/Tushar49/browser-userscripts`, `@version`, `@description`, `@match`, `@grant`, `@homepageURL` (folder URL), `@supportURL` (repo issues), `@license GPL-3.0-or-later`.
- `@require` must be pinned (`?version=N`); floating `?download` is forbidden (supply-chain drift).
- GreasyFork 599400 syncs from raw GitHub URL of the `.user.js` file — push to `main` triggers sync via push webhook.
- GreasyFork long description: `greasyfork-description.md` + `greasyfork-description.html` are the verbatim Admin-tab sync sources (raw URL + HTML/Markdown radio). NEVER edit the description on the GreasyFork site — edit the file, push, re-sync.
- Before writing or rewriting a `greasyfork-description.*` file, ASK the user: Markdown (cheap, portable, native table/fenced-code render via Redcarpet) or HTML (hero cards, badges, styled chips — but the sanitizer strips ALL CSS except `border`, `background-color`, `color`; no `<style>` blocks, no dark/light media queries). Get an explicit pick.
- HTML description rule: EVERY `<code>` chip and `<th>` MUST set BOTH `background-color` + `color` inline. GreasyFork flips body text per theme but keeps our chip bg fixed, so bg-only chips go invisible (2026-10-10 bug: `#eaeef2` bg + inherited white text in dark mode). Dark-safe chip: `background-color: #3d444d; color: #ffffff;`. Never use `#eaeef2`/`#f6f8fa` bgs.
- License: TimerHooker lineage is GPL — new scripts in this family stay `GPL-3.0-or-later`. Root `LICENSE` is still MIT placeholder — replace with full GPL-3.0 text before calling license done.

## ANTI-PATTERNS (THIS PROJECT)

- NEVER edit `2026-carcass.user.js` (verbatim diff reference).
- NEVER use `innerHTML` / `outerHTML` / remote assets (fonts, icons, CSS) in script body — `textContent` + pure CSS only.
- NEVER commit unless explicitly requested.
- NEVER commit local state: `.omo/`, `.codegraph/`, editor dirs, caches, `*.tmp/*.bak`, `.env` (see `.gitignore`).
- NEVER suppress with `as any` / `@ts-ignore` (no TS here, but rule stands for snippets).

## COMMANDS

```powershell
# Validate userscript syntax (LSP typescript declined — this is the validator)
node --check tampermonkey/timerhooker-ultimate/timerhooker-ultimate.user.js

# Git (cred manager handles auth; no gh CLI installed)
git status --short
git log --oneline -10
```

No build, no tests, no package manager in this repo.

## NOTES

- Env: win32 + pwsh. Bash tool: pass `workdir`, never `cd`. `tail`/`wc` don't exist. `Select-String -Path` has no `-Recurse`/`-Include` — use `default.grep` for content search, `default.glob` for file search.
- Comment-hook fires on banner/header comments — the GPL lineage banner in the release file is required, keep it.
- GitHub API unauthenticated from shell — webhook checks need browser or `gh auth login`.
- Open QA: manual 8x test (YouTube SPA nav, late-added media, CSP-strict page, toast timing) not yet done; GreasyFork long description still needs Usage/Shortcuts paste.
