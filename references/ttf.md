# SDL_ttf — 7Games/zig-sdl3

Enable `.ext_ttf = true`; use `try sdl.ttf.init()` and `sdl.ttf.quit()` around
all font and text objects. Fonts use `Font.init`/`deinit`. The binding includes
surface, renderer and GPU text engines plus `Text` objects; there is no generic
root `sdl.ttf.renderText` shortcut.

Destroy texts before their text engine and fonts, and destroy renderer/GPU text
engines before their graphics owner. Font methods such as `renderTextBlended`
return owned surfaces. Inspect size, encoding and return-type contracts before
writing an example. Plan Unicode shaping, fallback fonts and DPI behavior in
the UI layer; keep text rendering outside authoritative simulation.

Pinned source: [src/ttf.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/ttf.zig), [build.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/build.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
