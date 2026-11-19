# Windows and graphics contexts — 7Games/zig-sdl3

`try sdl.video.Window.init(title, width, height, flags)` returns a `Window`
value; its dimensions are `usize`. Destroy the owned window with
`window.deinit()`. Common flags include `.resizable` and `.high_pixel_density`.

`window.getSize()` and `window.getSizeInPixels()` return fallible result structs;
inspect their fields rather than passing output pointers. Use pixel dimensions
for framebuffers and window coordinates for interaction. Resize and display
scale events require refreshing dependent presentation state.

OpenGL lives under `sdl.video.gl`, including `Context.init(window)`, attribute
configuration and swap operations. Inspect fallible context teardown before
writing defer cleanup. Window flags alone do not create GPU devices. SDL GPU window claims belong to `sdl.gpu.Device` and must be released before the window is destroyed.

Pinned source: [src/video.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/video.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
