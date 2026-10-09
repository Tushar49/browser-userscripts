# 🚀 TimerHooker Ultimate

Control page timer speed | Speed up to skip page timing ads | Video + audio fast forward (slow play) | Skip ads | SPA-safe | Support almost all web pages.

Ultimate merge of the TimerHooker family: **2026 functional base + TSun UX ideas reimplemented safely**, with supply-chain and hardening fixes. GPL-3.0-or-later.

Fork lineage: Cangshi original (372673) → Tiger 27 English 1.2.1 (438894) → TSun 1.2.6 UI inspiration (543709) → rehan 2026 1.4.2 direct base (553657).

## ✨ What it does

- Hooks `setTimeout` / `setInterval` / `Date` so page countdowns, ads, and time-gates run at your speed.
- Speeds `video` **and** `audio` (`playbackRate`, hidden from page via lying getter), including late-added players via `MutationObserver` + shadow-DOM sweep.
- Floating energy ball (left side): hover to reveal `>` `<` `>>` `<<` `O` + click bubble for custom speed.
- Glass toast pill (bottom): shows `Speed: 2.00x`, auto-hides in 2s, respects `prefers-reduced-motion`, ARIA live.
- Survives YouTube / SPA navigation (`ensureUIAlive` + `yt-navigate-finish` + `spfdone` + 1.5s watchdog).
- Syncs speed to iframes via validated `postMessage`.

## 🛠️ Installation

1. Install a userscript manager: **Tampermonkey** (recommended), Violentmonkey, or Greasemonkey.
2. Install `timerhooker-ultimate.user.js`:
   - dev: Tampermonkey Dashboard → `+` → paste file → Save.
   - release: GreasyFork page (URL TBD after publish) → Install.
3. Open any site — the ball appears on the left. Hover → pick speed. Badge shows current multiplier.

Requires `Everything-Hook` library (pinned `@require ...?version=881251`).

## 🕹️ Usage

| Action | Button | Shortcut |
|---|---|---|
| Custom speed (prompt) | click `x1.00` bubble | Ctrl/Alt + 9 |
| +2 additive | `>` | Ctrl + `=` |
| −2 additive | `<` | Ctrl + `-` |
| ×2 multiply | `>>` | Alt + `=` |
| ÷2 divide | `<<` | Alt + `-` |
| Reset 1x | `O` | Ctrl/Alt + 0 |

Buttons are keyboard-focusable (Tab + Enter/Space).

## 🔒 Security notes

- `@grant none`, page-context (`@inject-into page`), zero `innerHTML`, zero remote images/scripts.
- Iframe messages validated (object + type + finite number + 0.0625–16 clamp).
- Watchdog timers use native (unhooked) `setTimeout/setInterval` so they never speed up.
- Scope: `*://*/*` by default. Narrow `@match` to sites you use; avoid banking/exam pages (lying `Date` can trip anti-cheat).

## 📝 Changelog

See [CHANGELOG.md](./CHANGELOG.md).

## 👤 Credits

Cangshi (original) · Tiger 27 (English) · SaeedX302/TSun (toast/glass inspiration) · rehan (2026 base).
