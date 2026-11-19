# Properties and hints — 7Games/zig-sdl3

`try sdl.properties.Group.init()` creates an owned group; use `deinit()` for
cleanup. `Group.set` and `Group.get` use typed property values
(`sdl.properties.Property`); inspect their exact arguments rather than copying
zsdl's root `setStringProperty` calls. Global properties are borrowed. Use
`lock`/`unlock` as required and document cleanup of externally stored pointers.

Hints live under `sdl.hints`, with `Type`, `get`, `getBoolean`, `set`, and
`setWithPriority`. Verify hint tags and return types. Configure driver-sensitive
hints before subsystem initialization. Root `sdl.setAppMetadata` and
`setAppMetadataProperty` are available for application identity. Do not use
property groups as a replacement for typed engine configuration.

Pinned source: [src/properties.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/properties.zig), [src/hints.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/hints.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
