# Dialogs and system UI — 7Games/zig-sdl3

`sdl.dialog` wraps `showOpenFile`, `showOpenFolder`, `showSaveFile` and
`showWithProperties` using callbacks. Check generic callback and user-data
arguments in source. Keep callback state alive until completion, copy selected
paths when required and distinguish cancellation from failure.

Message boxes live under `sdl.message_box`; tray integration lives under
`sdl.tray`. Follow main-thread rules, parent-window lifetimes and callback
ownership. Do not block the simulation awaiting an OS dialog or hold engine
locks while UI callbacks run.

Pinned source: [src/dialog.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/dialog.zig), [src/message_box.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/message_box.zig), [src/tray.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/tray.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
