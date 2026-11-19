---
name: zig-sdl3
description: Use the pinned 7Games/zig-sdl3 API for SDL3 build integration, windows, tagged events, input, rendering, audio, and optional extensions in Zig. Apply when writing or reviewing SDL integration; do not substitute zig-gamedev/zsdl APIs.
---

# 7Games/zig-sdl3

This skill covers the 7Games/zig-sdl3 bindings, not zig-gamedev/zsdl. The API references use version 0.2.4, commit `f0500f824ff2768a3cc0ece2918df56576dde11c`, as their baseline. Inspect the consuming project's selected revision and compiler before applying examples; its dependency source takes precedence when signatures differ.

Upstream exports the module as `sdl3`. Examples use `sdl` as a local namespace and import key; match the module key configured by the consuming build.

## API and ownership rules

- Import `const sdl = @import("sdl");`. Use namespaces such as `sdl.video`,
  `sdl.events`, `sdl.render`, and `sdl.gpu`, preserving exported spelling.
- `sdl.events.poll()` returns `?sdl.events.Event`, a tagged union. Switch on
  the event and capture its payload. Keyboard scancodes/keycodes are optional;
  gamepad device payloads use `id`.
- Window and renderer constructors return wrapper values with `deinit()`;
  copying them does not create another owner. GPU resources instead use
  device release methods. Check each resource's exact destruction signature.
- Handle error unions with `try` or an explicit failure policy, including
  `Renderer.present`. Use `sdl.errors.get()` for SDL error details.
- `sdl.quit(flags)` releases subsystem references; `sdl.shutdown()` is global
  shutdown. Release native objects first. Keep platform/UI operations on their
  required thread and use `errdefer` for partial construction.
- SDL allocations and borrowed views have distinct contracts. Free transferred
  SDL buffers with `sdl.free`; keep application allocations with their original
  allocator. Never reset an arena while native callbacks or jobs reference it.
- Optional namespaces such as `image`, `ttf`, and `net` require matching build
  options; being exported does not mean an extension is linked.
- Test native display/audio integration separately from display-independent logic.

## Tagged event example

```zig
while (sdl.events.poll()) |event| {
    switch (event) {
        .key_down => |key| {
            if (key.scancode == .escape) {
                return;
            }
        },
        else => {},
    }
}
```

This fragment shows tagged payloads and optional scancodes; initialization and window ownership are covered separately.

## References

Read only the references needed for the task:

- [Build and first frame](references/getting-started.md)
- [Initialization and teardown](references/init-lifecycle.md)
- [Tagged events](references/events.md)
- [Binding conventions](references/binding-patterns.md)
- [Windows and graphics contexts](references/video-windows.md)
- [2D rendering](references/render.md)
- [SDL GPU](references/gpu.md)
- [Keyboard and text input](references/keyboard.md)
- [Mouse and cursors](references/mouse.md)
- [Gamepads and joysticks](references/gamepad-joystick.md)
- [Audio devices and streams](references/audio.md)
- [Allocator integration](references/allocator-integration.md)
- [Filesystem and I/O](references/filesystem-io.md)
- [Properties and hints](references/properties-hints.md)
- [Logging and errors](references/log-errors.md)
- [SDL_image](references/image.md)
- [SDL_ttf](references/ttf.md)
- [SDL_net](references/net.md)
- [Storage and save data](references/storage.md)
- [Camera capture](references/camera.md)
- [Dialogs and system UI](references/dialogs-ui.md)
- [Clipboard](references/clipboard.md)
- [Threads and synchronization](references/threading.md)
- [Platform and timing](references/system-platform.md)
- [Touch and pen](references/touch-pen.md)

Authority: [pinned upstream source](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c), [API docs](https://7games.codeberg.page/zig-sdl3/@docs).
