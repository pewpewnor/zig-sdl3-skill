# Tagged events — 7Games/zig-sdl3

`sdl.events.Event` is `union(sdl.events.Type)`. `sdl.events.poll()` returns
`?Event`; switch on the event itself and capture its payload.

```zig
while (sdl.events.poll()) |event| {
    switch (event) {
        .quit, .window_close_requested => return,
        .key_down => |key| {
            if (key.scancode == .escape) {
                return;
            }
        },
        .gamepad_added => |device| {
            const id = device.id;
            _ = id;
        },
        else => {},
    }
}
```

This fragment returns from a `void` event-processing function. `Keyboard.scancode`
and `Keyboard.key` are optional. Gamepad device payloads use `id`, not
`gdevice.which`. Do not access `event.type` or poll into a C-style output union.
Copy input into engine-owned actions; payload pointers and borrowed strings are
not durable command data. Inspect each payload's ownership contract before
retaining data from text, drop, clipboard, or user events.

Pinned source: [src/events.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/events.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
