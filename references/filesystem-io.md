# Filesystem and I/O — 7Games/zig-sdl3

Paths live under `sdl.filesystem`. `getBasePath()` returns a fallible borrowed
path; `getPrefPath(org, app)` returns a fallible owned sentinel slice that must
be freed with `sdl.free`. Do not infer ownership from the string type alone.

`io_stream.Stream` wraps SDL I/O with `init`, `read`, and `deinit` and additional
constructors; check mode, ownership and close-on-load parameters. SDL async I/O
is wrapped under `sdl.async_io`; drain or cancel outstanding work before freeing
buffers and queues. Keep save serialization and asset IDs independent of SDL.
Use the consuming compiler’s APIs when choosing Zig I/O instead.

Pinned source: [src/filesystem.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/filesystem.zig), [src/io_stream.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/io_stream.zig), [src/async_io.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/async_io.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
