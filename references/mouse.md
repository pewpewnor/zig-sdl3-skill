# Mouse and cursors — 7Games/zig-sdl3

`sdl.mouse.getState()` returns a tuple `{ ButtonFlags, f32, f32 }`, not an
output-pointer result. Use `getRelativeState` or
`setWindowRelativeMode` for relative motion, following their exact signatures.

Mouse button, motion and wheel events have typed payloads. Keep window,
renderer and framebuffer coordinates distinct; wheel movement is not an integer
button event. `sdl.mouse.Cursor` constructors create owned cursors with
`deinit()`; default/current cursor queries may return borrowed handles. Check
ownership before cleanup. Restore cursor/capture policy when focus changes.

Pinned source: [src/mouse.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/mouse.zig), [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
