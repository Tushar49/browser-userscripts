# timerhooker-ultimate — AGENTS.md

Covers only TimerHooker-specific hardening. Repo-wide rules live in root `AGENTS.md` — never repeat them here.

## OVERVIEW

Release file `timerhooker-ultimate.user.js` v2.0.0: 2026 engine (timer hooks, video+audio rate, MutationObserver, SPA survival) + TSun UX reimplemented safely (glass toast, body-guard mount).

## WHERE TO LOOK

| Task | Location | Notes |
|---|---|---|
| Timer math / clamps | release file — hook section | `0.0625`–`16` range; keep `16`/`0.065` clamp behavior |
| Media rescan / SPA | release file — Observer + `ensureUIAlive` | `yt-navigate-finish`, `spfdone`, 1.5s watchdog |
| postMessage sync | `listenParentEvent` / `sentChangesToIframe` | iframe speed sync |
| Reference diff | `2026-carcass.user.js` | read-only — diff against it, never edit |

## CONVENTIONS (THIS SCRIPT ONLY)

- UI timers must use natives: `THU_NATIVE_SET_TIMEOUT/INTERVAL` (UI poll 1500ms, media rescan, toast hide 2000ms, cover hide 100ms) — never hooked timers.
- `listenParentEvent` must validate: object + type + finite + clamp `0.0625..16`.
- `sentChangesToIframe` per-frame `try/catch`.
- Mount: `onReady` MutationObserver body-guard + `applyUI` double-mount guard + `ensureUIAlive` try/catch.
- Buttons (all 6): `title` + `tabindex=0` + `role=button` + Enter/Space handler; text glyphs only.
- Toast: pill bottom, `Speed: X.XXx`, auto-hide 2s, `prefers-reduced-motion`, ARIA live. Fullscreen cover stays secondary flash only.
- zIndex: container `2147483647`, toast `2147483646`.

## ANTI-PATTERNS (THIS SCRIPT)

- NEVER hooked `setTimeout`/`setInterval` for own UI timing (page speed would warp them).
- NEVER unvalidated `postMessage` (type/finite/clamp required).
- NEVER remote icons (icons8 hotlinks forbidden) or fullscreen-flash-as-primary feedback.
- NEVER `file://` match by default.

## COMMANDS

```powershell
node --check timerhooker-ultimate.user.js   # run from this dir
```

## NOTES

- Functionality must not regress vs carcass: only accepted deltas are `file://` default off + fullscreen flash demoted to secondary.
- Per-script `README.md` usage/shortcuts table is the GreasyFork long-description source.
