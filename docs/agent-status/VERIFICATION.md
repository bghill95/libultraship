# libultraship verification log

Result words: Passed, Failed, Blocked, Not Run. Only runs actually executed are entries, newest first; reading code is inspection, not testing. A result at one commit is never carried to a later one, and a command, time or environment that was not kept is `not recorded`, never reconstructed.

## Verification by branch head
Current state only; each cell names the commit its result is at.

| Branch | Head | Unit tests | CI: build-validation and tidy-format-validation | Independent review |
|---|---|---|---|---|
| enemy-sync-input | 4a83135 | Not Run: the repository has no unit tests | build-validation Failed at 4a83135 (Windows arm64; cited); tidy-format-validation Not Run at 4a83135 | Not Verified |

## VER-001: Records check
- Test name and purpose: Records check: the standard's checker on these records, for their form, hashes, paths and banned strings.
- Command or procedure: `python -I ~/projects/navideus-reporting-standard/main/scripts/check_records.py --repo .`, from the worktree root
- Commit tested: a draft of the files committed as a46d2f7, run uncommitted on 4a83135; the entry and Last verified were filled after the run
- Environment and configuration: the `libultraship` worktree on branch `agent-status`, Git Bash on Windows 11, Python 3.11.15, git 2.52.0.windows.1
- Execution date: 2026-10-26T06:49Z
- Result: Passed
- Evidence: exit 0: `PASS`, then `WARN AGENTS.md, CLAUDE.md, README.md: R3 not checked without --base`.
- Reviewer and disposition: none; Fable's verification follows
- Remaining failures, limitations or untested scenarios: the checker checks form, references and banned strings, not whether a claim is true; this run is without `--base`, so it skips R16 and R3 on AGENTS.md, CLAUDE.md and README.md, which the `--base` run after the commit covers (reported with the draft PR); no name list was set in `AGENT_STATUS_BANNED_WORDS`.
- Who ran it: Opus

## Cited results (not re-run)
| Check | Date | Commit | Environment | Result | Evidence |
|---|---|---|---|---|---|
| build-validation (GitHub Actions, run 28716809559 on the push of `enemy-sync-input`): Release builds of the library on macOS, Linux, Windows x64 and Windows arm64 | 2026-07-04T19:13Z | 4a83135 | GitHub-hosted runners macos-14, ubuntu-latest and windows-latest (`.github/workflows/build-validation.yml`) | Failed: GitHub's recorded conclusion for the run is failure; its build-windows-arm64 job failed in the "Build libultraship" step (job annotation: "Process completed with exit code 1."), cause not recorded (GitHub no longer serves the run's logs, checked 2026-10-26); build-macos, build-linux and build-windows-x64 succeeded; build-ios was skipped, disabled in the workflow | https://github.com/bghill95/libultraship/actions/runs/28716809559 |

## Not Run
| Check | Result | What it needs |
|---|---|---|
| tidy-format-validation at 4a83135: clang-format-14 over `src` and `include`, then clang-tidy on the changed lines | Not Run | a pull request (`.github/workflows/tidy-format-validation.yml`), or clang-format-14 run locally as `CONTRIBUTING.md` shows |
| Two-instance local co-op input: each window keeps its own gamepad while unfocused, and again after a hotplug | Not Run | a consumer game build with this library, two gamepads, and `Controllers.Port0GamepadOrdinal` set to 0 in one instance and 1 in the other (326a995) |
| Independent review at 4a83135 | Not Run | a reviewer separate from the implementer and a recorded disposition |
