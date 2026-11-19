# Clipboard — 7Games/zig-sdl3

Clipboard operations live under `sdl.clipboard`: `getText`, `setText`,
`hasText`, MIME data and primary-selection helpers. `getText` returns owned
SDL text; copy or release it with `sdl.free` according to its contract. Setters
do not imply ownership transfer of arbitrary application buffers.

Custom MIME data callbacks require persistent state and a cleanup callback;
inspect when SDL calls each callback and how returned buffers are owned. Keep
clipboard interaction on the required UI thread. Treat pasted content as
untrusted input and apply the destination editor's size/encoding constraints.

Pinned source: [src/clipboard.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/clipboard.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
