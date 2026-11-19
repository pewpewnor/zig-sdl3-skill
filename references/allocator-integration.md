# std.mem.Allocator integration — 7Games/zig-sdl3

`sdl.allocator` adapts SDL allocation to `std.mem.Allocator`; `sdl.free`
releases SDL-returned memory. A project allocator must free only its own
allocations. Inspect each returned string/slice to distinguish owned buffers
from borrowed views before registering cleanup.

`sdl.setMemoryFunctionsByAllocator(allocator)` installs allocator-backed global
SDL callbacks and returns previous callbacks. Set this up before SDL allocation,
keep its allocator alive and thread-safe for every SDL user, and restore
callbacks only after all allocations using them have been released. This is a
global integration choice, not a per-window or per-frame convenience.

Do not use a resettable frame arena for arbitrary SDL allocations. The adapter
ignores requested alignment in its low-level allocation implementation, so do
not assume it satisfies arbitrary over-aligned Zig types. Prefer explicit
engine allocator ownership while leaving SDL's allocator untouched unless the
integration has a concrete requirement and lifecycle validation.

Pinned source: [src/sdl3.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/sdl3.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
