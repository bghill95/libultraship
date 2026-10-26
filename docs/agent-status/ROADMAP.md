# libultraship roadmap

Each item under Planned milestones and Future development ideas carries one label: [confirmed by owner] (the owner's word, with its date and source), [approved by record] (an owner decision written in the repository, cited) or [suggestion] (an agent's proposal, not approved). Priorities come from the owner, never from commit activity. A section with nothing on record holds exactly: No roadmap is recorded for this project; none is invented.

## Current milestone
No roadmap is recorded for this project; none is invented.

## Confirmed priorities
No roadmap is recorded for this project; none is invented.

## Planned milestones
No roadmap is recorded for this project; none is invented.

## Dependencies
- Upstream: libultraship, https://github.com/Kenix3/libultraship (root `README.md`), the library this fork's change sits on; these records do not compare this branch's history with upstream's.
- Third-party libraries listed in the root `README.md`, among them SDL2, whose joystick hint and game-controller calls the co-op change uses; on Windows with `USE_AUTO_VCPKG` the build installs SDL2, libzip, tinyxml2, spdlog and others through vcpkg (`cmake/dependencies/windows-vcpkg.cmake`).
- Consumer: the sibling repository https://github.com/bghill95/OOT-True-Co-op pins this repository as its `libultraship` submodule at 4a83135 on its `enemy-sync` branch (checked 2026-10-26), so a change here reaches it only when that pin moves.

## Known risks
- The `build-validation` run at 4a83135 failed on Windows arm64, cause not recorded (`VERIFICATION.md`).

## Future development ideas
No roadmap is recorded for this project; none is invented.
