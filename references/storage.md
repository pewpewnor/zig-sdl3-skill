# Storage and save data — 7Games/zig-sdl3

SDL storage is wrapped by `sdl.storage.Storage`, including `initTitle`,
`initUser`, and `initFile`. Inspect each constructor's arguments and access
permissions. Wait for `ready()` before reading or writing and handle fallible
`deinit()` explicitly according to the source signature.

Use `readFile`/`writeFile` and directory operations through the storage object;
check required buffer sizes and result ownership. Keep serialization versioning,
validation, atomic replacement and conflict policy in a separate save module.
A storage handle alone does not establish cloud authentication or conflict
resolution. Directory result buffers and `storage.Path` have their own cleanup
contracts.

Pinned source: [src/storage.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/storage.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
