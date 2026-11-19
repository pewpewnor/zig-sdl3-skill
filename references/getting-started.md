# Build and first frame — 7Games/zig-sdl3

Add 7Games/zig-sdl3 through Zig package management and choose a revision compatible with the application's compiler. Upstream exports `sdl3`; the consuming build chooses its import key:

```zig
const zig_sdl3 = b.dependency("zig-sdl3", .{
    .target = target,
    .optimize = optimize,
});
exe.root_module.addImport("sdl", zig_sdl3.module("sdl3"));
```

This fragment assumes `b`, `target`, `optimize` and `exe` already exist.
The dependency prepares translated C declarations and links
SDL built from source by default; do not copy zsdl's manual linking recipe.
System SDL is selected by the dependency's system integration option `sdl`,
not by inventing a `.system_sdl` dependency option. Verify deployment of any
shared libraries for the target. Extension dependency options such as
`.ext_image = true` and `.ext_ttf = true` are booleans; the internal
`SdlConfig.ext_*` fields are optional option structs, a different interface.

For window and drawing calls, read [windows](video-windows.md) and [rendering](render.md).

Pinned source: [build.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/build.zig), [examples/hello-world.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/examples/hello-world.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
