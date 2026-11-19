# Binding conventions — 7Games/zig-sdl3

Import `const sdl = @import("sdl");`. Public declarations live in namespaces:
`sdl.video.Window`, `sdl.render.Renderer`, `sdl.events.Event`, `sdl.gpu.Device`.
Methods receive wrapper values, often containing a native `value` field. Copying
a wrapper does not acquire ownership; give each native resource one owner.

Use exact return types from source: many constructors and operations return
error unions, some queries return optionals or plain values. `Renderer.present`
is fallible. Even cleanup is not universally infallible (`video.gl.Context.deinit`
returns `!void`). Handle each signature explicitly.

The public `sdl.c` namespace exists, but prefer the Zig facade. Keep deliberate
raw-C adapters isolated and documented rather than mixing them into game logic.
Never transplant zsdl top-level calls, `EventType`, `FRect`, or opaque pointer
ownership conventions into this wrapper. Read the pinned implementation when
upstream prose or examples disagree with signatures.

Pinned source: [src/sdl3.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/sdl3.zig), [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig), [src/video.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/video.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
