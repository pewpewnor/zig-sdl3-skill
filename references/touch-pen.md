# Touch and pen — 7Games/zig-sdl3

Touch enumeration is available under `sdl.touch`; pen declarations live under
`sdl.pen`. Handle tagged finger/pen events through `sdl.events.Event` and
capture the corresponding payload. Inspect field names in the pinned event
structs rather than reading zsdl's `tfinger`, `pmotion` or `paxis` members.

Track touch contacts by device and finger identity. Convert normalized touch
positions to the intended coordinate space and account for window scale.
Pressure, axis support and emulated mouse events differ by device; deduplicate
according to input policy. Copy persistent interaction state into engine-owned
storage, keeping native events outside gameplay.

Pinned source: [src/touch.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/touch.zig), [src/pen.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/pen.zig), [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
