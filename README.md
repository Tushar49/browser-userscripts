# browser-userscripts

Monorepo for userscripts (Tampermonkey/Violentmonkey) + dev-console snippets.

Repo: https://github.com/Tushar49/browser-userscripts

## Layout

```text
browser-userscripts/
  README.md
  LICENSE (GPL-3.0-or-later)
  tampermonkey/
    _template/                  (future: new-script skeleton)
    timerhooker-ultimate/
      timerhooker-ultimate.user.js  (release file, v2.0.0)
      2026-carcass.user.js          (verbatim 2026 1.4.2 reference, do not edit)
      README.md
      CHANGELOG.md
  console/                      (devtools snippets — not userscripts)
```

## Scripts

| Script | What | Source | Install |
|---|---|---|---|
| TimerHooker Ultimate | timer/video+audio speed, ad-skip, SPA-safe | [tampermonkey/timerhooker-ultimate](./tampermonkey/timerhooker-ultimate/) | [GreasyFork 599400](https://greasyfork.org/en/scripts/599400-timerhooker-ultimate) |

## Conventions

- One folder per script: `<slug>/<slug>.user.js` + `README.md` + `CHANGELOG.md`.
- Userscript header: `@name`, `@namespace https://github.com/Tushar49/browser-userscripts`, `@version`, `@description`, `@match`, `@grant`, `@homepageURL` (folder), `@supportURL` (issues), `@license`.
- GreasyFork syncs from raw GitHub URL of the `.user.js` file.
- GPL-3.0-or-later (TimerHooker parents are GPL).
