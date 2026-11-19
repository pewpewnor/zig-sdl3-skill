# Threads and synchronization — 7Games/zig-sdl3

SDL threads, mutexes, conditions, semaphores, read/write locks and atomic
operations are wrapped. Use `sdl.thread.Thread` and `sdl.mutex` types only with
their actual lifecycle signatures; thread completion/joining is not a universal
`deinit()` operation. Inspect constructors before use, including upstream
signature defects, rather than assuming every type is interchangeable.

Keep event
polling, window lifecycle and presentation on the permitted thread. Worker
state and callback buffers must outlive all work; join before freeing them.
Never share a reset arena across pending jobs or hold a worker lock across UI
callbacks. SDL's existence does not make every subsystem call thread-safe.

Pinned source: [src/thread.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/thread.zig), [src/mutex.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/mutex.zig), [src/atomic.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/atomic.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
