# libultraship decisions

Append only, oldest first. An entry is never rewritten: when a later decision replaces it, its Status becomes Superseded and it gains a last line `- Superseded by: DEC-nnn`. Alternatives and rationale come only from the cited record; where the record states none, the field reads `not recorded`. The entries cover the local co-op input change, 326a995 and 4a83135, from their commit messages; decisions in the branch's earlier history are not repeated here. Dates are the commits' UTC dates.

## DEC-001: Keep gamepads reporting in unfocused windows, on every graphics backend
- Date: 2026-07-04
- Status: Accepted
- Context: two game instances on one PC need each window tied to its own physical gamepad regardless of OS focus, and only one window can hold focus; the DX11 path never set SDL's background events hint, only the SDL GL and Metal paths did (the commit message of 326a995 and the comment it adds).
- Decision: set `SDL_HINT_JOYSTICK_ALLOW_BACKGROUND_EVENTS` before the game-controller subsystem starts, in `osContInit` in `src/libultraship/libultra/os.cpp`, independent of the graphics backend.
- Alternatives considered: not recorded
- Rationale: so pads keep reporting in unfocused windows on every graphics backend (the commit message of 326a995).
- Consequences: the hint is set unconditionally in `osContInit` (inspection of 326a995, not a test); no test result is recorded for it (`VERIFICATION.md`).
- References: 326a995; `src/libultraship/libultra/os.cpp`

## DEC-002: Pin port 1 to one gamepad by its ordinal, opt-in through the config
- Date: 2026-07-04
- Status: Accepted
- Context: each of two game instances on one PC must own one pad, while by default every connected pad drives port 1 (the commit message of 326a995 and the comment it adds).
- Decision: a new config integer, `Controllers.Port0GamepadOrdinal`, default -1 for the stock behavior; when 0 or more, port 1 binds only the Nth connected gamepad and ignores the rest, so instance A pins pad 0 and instance B pins pad 1 (`src/ship/controller/physicaldevice/ConnectedPhysicalDeviceManager.cpp`).
- Alternatives considered: not recorded
- Rationale: so that each game instance can own one pad, while -1 keeps the stock behavior (the commit message of 326a995).
- Consequences: 4a83135 then rebuilds the port-0 pad-pinning ignore set on every gamepad refresh, because instance ids change on every replug and stale entries left the rightful pad ignored after a hotplug shifted the ordinals (its commit message, which cites "review finding #4"); no test result is recorded (`VERIFICATION.md`).
- References: 326a995, 4a83135; `src/ship/controller/physicaldevice/ConnectedPhysicalDeviceManager.cpp`
