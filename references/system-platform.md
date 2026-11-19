# Platform and timing — 7Games/zig-sdl3

Timing lives under `sdl.timer`: `getMillisecondsSinceInit`,
`getNanosecondsSinceInit`, `getPerformanceCounter`, `getPerformanceFrequency`,
`delayMilliseconds`, and nanosecond delay variants. Do not copy zsdl's root
`getTicksNS` or `delay` calls. Use monotonic elapsed time for frame pacing and a
fixed-step accumulator with bounded catch-up for simulation.

Platform, CPU, power, locale, date/time and OS integration have public wrappers
(`sdl.platform`, `sdl.cpu_info`, `sdl.PowerState`, `sdl.Locale`, `sdl.time`,
`sdl.system`). Inspect each capability's availability and ownership per target.
Compile-time target checks do not establish runtime graphics support. Test native display integration separately from display-independent logic.

Pinned source: [src/timer.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/timer.zig), [src/platform.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/platform.zig), [src/system.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/system.zig), [src/cpu_info.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/cpu_info.zig), [src/power.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/power.zig), [src/locale.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/locale.zig), [src/time.zig](https://codeberg.org/7Games/zig-sdl3/src/commit/f0500f824ff2768a3cc0ece2918df56576dde11c/src/time.zig). Baseline and validation policy: [SKILL.md](../SKILL.md).
