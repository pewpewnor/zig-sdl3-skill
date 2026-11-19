# SDL_image — 7Games/zig-sdl3

Enable `.ext_image = true` on the `zig-sdl3` dependency before using
`sdl.image`. The namespace is exported even when extension linking is disabled.
`loadFile` produces a surface; `loadTexture` produces a renderer texture.
Destroy each owned surface/texture through its wrapper `deinit()`.

Animation and typed-I/O loaders are also wrapped. Verify format-specific build
options (`image_enable_png`, etc.) rather than promising every codec. Check
close-stream parameters and who owns animation frames. Decode/upload lifetimes
must not retain a reset arena. SDL_image availability does not imply SDL_ttf
or SDL_mixer was enabled.

Pinned source: [src/image.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/image.zig), [build.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/build.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
