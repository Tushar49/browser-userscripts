# Changelog — TimerHooker Ultimate

## 2.0.0 — Ultimate merge

- Base: 2026 1.4.2 carcass (`2026-carcass.user.js` preserved verbatim for diffing).
- Header: renamed to TimerHooker Ultimate, pinned `@require ...Everything-Hook.js?version=881251`, dropped floating `?download` + `file://` default, added `@homepageURL/@supportURL`.
- UI: glass toast pill (pure CSS, `textContent`-only, ARIA live, `prefers-reduced-motion`); kept fullscreen cover as secondary flash.
- Mount: `onReady` body-guard (MutationObserver until `document.body`) + `applyUI` double-mount guard + `ensureUIAlive` try/catch + SPA events.
- Timers: native `THU_NATIVE_SET_TIMEOUT/INTERVAL` for UI poll (1500ms), media rescan, toast hide (2000ms), cover hide (100ms).
- Sync: `listenParentEvent` validates object/type/finite/clamp `0.0625..16`; `sentChangesToIframe` per-frame try/catch.
- A11y: `title` + `tabindex=0` + `role=button` + Enter/Space on all 6 buttons; text glyphs only, no remote icons.
- Policy: zero `innerHTML`/`outerHTML`/remote assets in script body; container `zIndex 2147483647`, toast `2147483646`.
- Unchanged: all timer-hook math, `16`/`0.065` clamps, shortcut keycodes, plugin name `timer`.
