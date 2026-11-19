# Gamepads and joysticks — 7Games/zig-sdl3

`sdl.gamepad.getGamepads()` returns `![]sdl.joystick.Id`; release the SDL-owned
slice through the allocator required by its source contract (`sdl.free`).
Open a device with `sdl.gamepad.Gamepad.init(id)` and call `deinit()` once for
each successful open. Joystick support lives in `sdl.joystick`.

Discover already-connected devices at startup as well as handling
`.gamepad_added` and `.gamepad_removed`. Both device-event payloads use `.id`.
Track handles by stable instance ID, not enumeration index, and close them on
removal and shutdown. `getAxis`/`getButton` are methods on the wrapper.

Translate mapped buttons and axes into domain actions. Specify dead zones,
trigger ranges and disconnect behavior; do not expose SDL handles in gameplay.
Advanced sensor, rumble and touchpad operations exist but require checking the
device's capabilities and the pinned method signatures.

Pinned source: [src/gamepad.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/gamepad.zig), [src/joystick.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/joystick.zig), [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
