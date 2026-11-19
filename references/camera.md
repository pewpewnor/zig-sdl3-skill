# Camera capture — 7Games/zig-sdl3

Camera discovery and capture are wrapped under `sdl.camera`: `getCameras`,
`Id` queries, `Camera.init`/`deinit`, permission-state queries and frame
acquisition/release. Initialize the camera subsystem deliberately.

Permission may be pending or denied even after opening; process camera events
and inspect permission state. Every acquired frame must be returned through
`releaseFrame` before camera teardown. Frame surfaces are borrowed for that
acquisition; do not destroy them as independently owned surfaces. Respect
format, pitch and timestamps when copying into engine buffers.

Pinned source: [src/camera.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/camera.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
