# Logging and errors — 7Games/zig-sdl3

SDL errors are available through `sdl.errors.get()` and `clear()`. Check
fallible facade operations with `try` or a deliberate error policy. Retrieve
error text at the failure site; do not treat stale SDL error text as proof that
a successful operation failed.

Logging lives in `sdl.log`; inspect the exported category, priority and callback
signatures before replacing its output. The dependency's
`log_message_stack_size` option controls its formatting stack buffer. Avoid
logging floods from input loops or audio callbacks. Preserve useful context
when translating SDL errors into engine errors.

Pinned source: [src/log.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/log.zig), [src/errors.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/errors.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
