# SDL_net — 7Games/zig-sdl3

Enable `.ext_net = true`; initialize with `try sdl.net.init()` and pair it with
`sdl.net.quit()` after all network resources have been released. The binding
exposes `Address`, `Server`, `StreamSocket`, and `DatagramSocket`.

Addresses use reference counting (`ref`/`unref`), not a universal `deinit()`.
Sockets and servers have their own teardown methods. Name resolution and
connections can be pending: inspect `Status`, timeout and polling operations;
do not equate construction with readiness. Define framing, bounds,
authentication and replay/replication policy in engine networking code, separate
from transport. SDL_net is optional and imposes no dependency on headless
simulation unless explicitly selected.

Pinned source: [src/net.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/net.zig), [build.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/build.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
