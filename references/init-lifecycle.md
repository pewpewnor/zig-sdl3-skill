# Initialization and teardown — 7Games/zig-sdl3

`try sdl.init(flags)` acquires subsystem references. `sdl.quit(flags)` releases
those references; `sdl.shutdown()` performs global SDL shutdown. These are
separate operations. Register global shutdown first, then subsystem teardown,
then object cleanup so defers run in reverse acquisition order.

```zig
defer sdl.shutdown();
const flags: sdl.InitFlags = .{ .video = true, .events = true };
try sdl.init(flags);
defer sdl.quit(flags);
```

The root also exports the `sdl.Init` lifecycle helper; inspect `Init.zig` before
using its managed subsystem ownership. Keep windows, event pumping, and UI on
the main thread. Do not let multiple platform owners shut down global SDL while
other objects remain live. Use `errdefer` for partial initialization.

Pinned source: [src/sdl3.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/sdl3.zig), [src/Init.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/Init.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
