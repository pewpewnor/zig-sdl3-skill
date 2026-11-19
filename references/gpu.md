# SDL GPU — 7Games/zig-sdl3

SDL GPU is wrapped by `sdl.gpu`. `Device.init` constructs an owned device;
`device.deinit()` destroys it. Device methods create resources and claim windows.
Use matching `releaseBuffer`, `releaseTexture`, `releaseShader`, pipeline,
sampler, transfer-buffer and fence methods rather than inventing resource
`deinit()` methods. Release a claimed window with `releaseWindow`.

Command buffers expose pass creation and submission. End passes before
submission; follow acquire/submit/cancel and transfer map/unmap contracts.
Swapchain acquisition may fail or yield no texture; inspect the actual return
type. Probe shader formats and presentation support rather than assuming a
backend exists on every machine.

Shader binaries must match the device backend and supported shader formats. Use the consuming application’s shader compiler and resource layout contracts.

Pinned source: [src/gpu.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/gpu.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
