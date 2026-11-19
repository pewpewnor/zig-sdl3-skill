# Audio devices and streams — 7Games/zig-sdl3

SDL3 audio is built around `sdl.audio.Device` and `sdl.audio.Stream`.
Devices use `open`/`close`; streams use `init`/`deinit`. For the simplified
path, `Device.openStream` returns a stream whose destruction also closes its
device. Inspect the callback type and starting paused state; resume through the
appropriate stream/device method after setup.

`Stream.putData`, `getData`, `flush` and format operations are wrapped. PCM
formats and `audio.Spec` must match the intended channel layout and sample rate.
Keep callback data alive until the callback can no longer run. Audio callbacks
need bounded work with no blocking I/O or ordinary allocation. WAV loading and
sample conversion may return owned buffers: follow the source's freeing rules.
SDL_mixer is a separate optional extension enabled with `.ext_mixer = true`.

Pinned source: [src/audio.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/audio.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
