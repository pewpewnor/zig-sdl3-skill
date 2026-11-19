# 2D rendering — 7Games/zig-sdl3

Create a renderer using `try sdl.render.Renderer.init(window, null)` and
release it with `renderer.deinit()` before releasing its window.

```zig
try renderer.setDrawColor(.{ .r = 20, .g = 24, .b = 32, .a = 255 });
try renderer.clear();
try renderer.present();
```

Texture creation belongs to the renderer (`createTexture`,
`createTextureFromSurface`); owned `sdl.render.Texture` values have `deinit()`.
Drawing uses renderer methods such as `renderFillRect`, `renderTexture`, and
`renderGeometry`. Rectangle and pixel types live under `sdl.rect` and
`sdl.pixels`; inspect exact type names and format tags before use.

Respect texture lock/unlock lifetimes and returned row pitch. Renderer logical
presentation, coordinate conversion, scale and clipping are separate from
simulation coordinates. SDL Renderer and SDL GPU are separate rendering APIs; choose the one required by the application.

Pinned source: [src/render.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/render.zig), [src/rect.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/rect.zig), [src/pixels.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/pixels.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
