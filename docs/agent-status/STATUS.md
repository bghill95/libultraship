# libultraship status

## Project and repository
libultraship: a library meant to provide reimplementations of libultra (n64 sdk) functions that run on modern hardware (root `README.md`).
Repository: https://github.com/bghill95/libultraship (public, default branch `enemy-sync-input`).
Fork: a fork of libultraship, https://github.com/Kenix3/libultraship (the upstream that the root `README.md` links), carrying a local co-op input change on its default branch `enemy-sync-input`. Its GitHub description reads "libultraship fork with local co-op input isolation (per-instance gamepad pinning) for OOT True Coop"; GitHub does not list it as a fork (no parent repository, checked 2026-10-26).
History: the branch's two newest commits, 326a995 and 4a83135 (2026-07-04), hold the local change; below them are 1,111 earlier commits, from e5d300c (2021-08-09) to 17a0b79 (2025-11-02). The remote holds no upstream branch, so these records do not compare that history with upstream's.
Use: a sibling repository, https://github.com/bghill95/OOT-True-Co-op, names this repository in its README as the `libultraship` submodule it pulls in from branch `enemy-sync-input`, and its `enemy-sync` branch pins that submodule at 4a83135 (checked 2026-10-26). No file or commit in this repository names that repository; the commit message of 326a995 describes two game instances (`soh.exe`) on one PC.

## Business Context
- Project type: Personal
- Parent product: Not applicable
- Component role: Not applicable
- Related repositories: Not applicable
- Commercialization status: Not applicable
- Client ID: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Engagement ID: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Compensation model: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Contract status: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Contract reference: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Commercial owner: Not Applicable (Personal by the owner's classification, 2026-10-25)
- Associated business deliverables: None recorded
- Current work billing status: Non-billable
- This change's billing class: Non-billable (documentation only)
- Source of classification and date confirmed: the owner's classification, 2026-10-25

## Lifecycle status
Paused (project status, not a technical state; a planning seed of the Navideus Agent Reporting Standard v1.1 rollout, 2026-10-25, not yet confirmed by the owner. The repository records no pause and no reason for one, and is consistent with it: no commit since 4a83135 on 2026-07-04; no other branch, issue or pull request before these records; not archived on GitHub; checked 2026-10-26)

## Development phase
Recorded as Paused (unconfirmed, see Lifecycle status) after the local co-op input change, 326a995 and 4a83135 (2026-07-04): it sets SDL's background joystick events hint in `src/libultraship/libultra/os.cpp`, and in `src/ship/controller/physicaldevice/ConnectedPhysicalDeviceManager.cpp` pins port 1 to one gamepad by its ordinal, read from the config key `Controllers.Port0GamepadOrdinal` (default -1, the stock behavior). Last known state: that change at 4a83135, for which the `build-validation` push run of 2026-07-04 recorded success on macOS, Linux and Windows x64 and failure on Windows arm64, cause not recorded (`VERIFICATION.md`).

## Current milestone
No milestone is recorded in this repository.

## Implementation status
A block for the default branch and for each branch holding unmerged work, at most three; every other branch is one line above the first block. States per README.md "Lifecycle states", revisions per "Revision traceability". Dates are UTC. Apart from the records' own `agent-status` branch, which has no block, the remote holds one branch, `enemy-sync-input`.

### enemy-sync-input
- Head: 4a83135 (2026-07-04), the default branch
- Last code commit: 4a83135 (2026-07-04): rebuilds the port-0 pad-pinning ignore set on every gamepad refresh, since instance ids change on every replug (its commit message)
- Implemented: yes, at 326a995 and 4a83135: the SDL hint that lets gamepads report to unfocused windows, set on every graphics backend, and an opt-in pin by which port 1 binds only the Nth connected gamepad when `Controllers.Port0GamepadOrdinal` is N (0 or more), so that each of two game instances on one PC can own one pad (the commit message of 326a995)
- Merged: is the default branch; 326a995 and 4a83135 were committed on it directly, with no merge commit
- Tested: Failed at 4a83135: GitHub Actions recorded the conclusion failure for the `build-validation` push run 28716809559 (2026-07-04T19:13Z), because its Windows arm64 job failed, cause not recorded (GitHub no longer serves the run's logs); its macOS, Linux and Windows x64 jobs succeeded (cited, not re-run; `VERIFICATION.md`); the repository has no unit tests, and no functional test of the co-op input is recorded
- Independently reviewed: Not Verified: the commit message of 4a83135 cites "review finding #4", whose reviewer and record are not in this repository
- Deployed: Not applicable: a library with no deployment environment of its own; a consumer compiles it into its game build (the sibling repository's pin at 4a83135, under Project and repository)
- Released: Not applicable: this fork has no release process of its own: no tags, no GitHub releases and no release workflow (checked 2026-10-26); the root `README.md` line "We use semantic versioning" is upstream's text on its API versioning and is not read as a release process of this fork

## Verification status
- Records check: Passed on a draft of the files committed as a46d2f7, run uncommitted on 4a83135 (VER-001, Opus)
- build-validation (GitHub Actions): Failed at 4a83135: the Windows arm64 build failed, cause not recorded; the macOS, Linux and Windows x64 builds succeeded (cited, `VERIFICATION.md`)
- tidy-format-validation (clang-format-14, clang-tidy): Not Run at 4a83135; it runs on pull requests only
- Two-instance co-op input test: Not Run; no result is recorded
- Independent review: Not Verified at 4a83135

## Open blockers
- None recorded.

## Next concrete engineering action
None is on record: the project is recorded as Paused (unconfirmed, see Lifecycle status) and resuming is the owner's decision. Resuming needs the CMake build in the root `README.md` (CMake 3.24 or later per `CMakeLists.txt`; on Windows the vcpkg option shown there) and a consumer game build to exercise the change, with `Controllers.Port0GamepadOrdinal` set per instance (326a995). Suggestion (agent, not approved): on resuming, re-run `build-validation` at the head, find the cause of the Windows arm64 failure, and record a two-instance, two-gamepad test in `VERIFICATION.md`.

## GitHub issue/PR links
- None: no issues, and no pull requests apart from the draft PR that carries these records, from branch `agent-status` (checked 2026-10-26).

## Revisions
- Default-branch commit: 4a83135 (2026-07-04)
- Implementation commit: 4a83135 (the co-op input change is 326a995 and 4a83135)
- Commit tested: 4a83135 (`build-validation`, Failed; cited from GitHub Actions, not re-run)
- Commit reviewed: Not Verified
- Commit deployed: Not applicable: a library with no deployment environment of its own
- Records revision: this commit

## Last verified
2026-10-26T06:49Z (Opus: the standard's checker on these records, VER-001; Fable's verification has not run yet)

## Uncertainties
- Paused is the planning seed, not confirmed by the owner; the reason for the pause is not recorded (the owner).
- The cause of the Windows arm64 build failure at 4a83135: GitHub no longer serves the run's logs (checked 2026-10-26); re-running the workflow would show it (the owner).
- Whether the co-op input change was tested with two instances and two gamepads, and who made the review that the commit message of 4a83135 cites (the owner).
- Which upstream commit the branch was taken from, and whether the change was offered upstream: these records do not compare the history with upstream's (the owner).
