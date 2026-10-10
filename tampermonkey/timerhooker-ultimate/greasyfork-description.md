🚀 TimerHooker Ultimate

Control page timer speed | Speed up to skip page timing ads | Video + audio fast forward | Skip ads | SPA-safe | Support almost all web pages.

Ultimate merge of the TimerHooker family: **2026 functional base + TSun UX ideas reimplemented safely**, with supply-chain and hardening fixes. GPL-3.0-or-later.

Fork lineage: Cangshi original (372673) → Tiger 27 English 1.2.1 (438894) → TSun 1.2.6 UI inspiration (543709) → rehan 2026 1.4.2 direct base (553657).

✨ Features

*   ⏱️ Timer Control: hooks `setTimeout` / `setInterval` / `Date` so countdowns, ads, and time-gates run at your speed.
*   🎬 Video + Audio: speeds `video` **and** `audio` (`playbackRate`, hidden from page), including late-added players via `MutationObserver` + shadow-DOM sweep.
*   🔮 Floating energy ball (left side): hover to reveal `>` `<` `>>` `<<` `O` + click bubble for custom speed.
*   🫧 Glass toast pill (bottom): shows `Speed: 2.00x`, auto-hides in 2s, respects `prefers-reduced-motion`, ARIA live.
*   🛡️ SPA survival: YouTube / SPA navigation via `ensureUIAlive` + `yt-navigate-finish` + `spfdone` + 1.5s watchdog.
*   🖥️ Iframe sync via validated `postMessage` (0.0625–16 clamp).

🛠️ Installation

1.  Install Tampermonkey (recommended), Violentmonkey, or Greasemonkey.
2.  Install from GreasyFork → open any site → the ball appears on the left.
3.  Requires `Everything-Hook` library (pinned `@require ...?version=881251`).

🕹️ Usage

| Action | Button | Shortcut |
|---|---|---|
| Custom speed (prompt) | click `x1.00` bubble | Ctrl/Alt + 9 |
| +2 additive | `>` | Ctrl + `=` |
| −2 additive | `<` | Ctrl + `-` |
| ×2 multiply | `>>` | Alt + `=` |
| ÷2 divide | `<<` | Alt + `-` |
| Reset 1x | `O` | Ctrl/Alt + 0 |

Buttons are keyboard-focusable (Tab + Enter/Space).

🔒 Security notes

*   `@grant none`, page-context, zero `innerHTML`, zero remote images/scripts in the script body.
*   Watchdog timers use native (unhooked) `setTimeout/setInterval` so they never speed up.
*   Scope `*://*/*` by default. Narrow `@match` for banking/exam pages (lying `Date` can trip anti-cheat).

👤 Credits

Cangshi (original) · Tiger 27 (English) · SaeedX302/TSun (toast/glass inspiration) · rehan (2026 base) · Source: https://github.com/Tushar49/browser-userscripts
