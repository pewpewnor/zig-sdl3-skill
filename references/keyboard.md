# Keyboard and text input — 7Games/zig-sdl3

`sdl.keyboard.getState()` returns `[]const bool` indexed by scancode values.
Pump events before querying current state and treat the returned slice as
borrowed. `sdl.Scancode` is the root scancode type; keycode declarations live
under `sdl.keycode`.

Use `.key_down`/`.key_up` payloads for transitions; their `scancode` and `key`
fields can be null. Ignore repeat for one-shot actions where appropriate. Use
text-input and composition events for Unicode text, not keycode-to-byte casts.
`keyboard.startTextInput`, `stopTextInput`, and text-area helpers take the
window as specified in source. Copy text into the UI owner's storage.

Pinned source: [src/keyboard.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/keyboard.zig), [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
