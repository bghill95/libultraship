# libultraship verification log

Result words: Passed, Failed, Blocked, Not Run. Only runs actually executed are entries, newest first; reading code is inspection, not testing. A result at one commit is never carried to a later one, and a command, time or environment that was not kept is `not recorded`, never reconstructed.

## Verification by branch head
Current state only; each cell names the commit its result is at.

| Branch | Head | Unit tests | CI: build-validation and tidy-format-validation | Independent review |
|---|---|---|---|---|
| enemy-sync-input | 4a83135 | Not Run: the repository has no unit tests | build-validation Failed at 4a83135 (Windows arm64; cited); tidy-format-validation Not Run at 4a83135 | Not Verified |

## VER-002: Fable's verification of these records
- Test name and purpose: Fable's verification of these records against the repository: the rollout verification checklist (checker, hashes and dates, lifecycle claims, Business Context values, pilot leakage, roadmap labels, ceilings, diff scope, the PR).
- Command or procedure: `python -I ~/projects/navideus-reporting-standard/main/scripts/check_records.py --repo . --base origin/enemy-sync-input` with the banned-words variable set at run time, then `git log -1` on every cited hash, `git branch -r`, `gh pr list --state all`, `gh issue list --state all`, and a read of every cited document.
- Commit tested: 5088211 (the records as they stood before this entry's commit; later record edits are outside this disposition)
- Environment and configuration: the owner's PC, Git Bash, Python 3.11, git 2.52, gh 2.86; the checklist was run by a read-only verification subagent on Fable's behalf, and Fable read its report.
- Execution date: 2026-10-26T07:47Z
- Result: Passed after fix round 1 (the cited CI run named by its identifier and labelled GitHub's conclusion with the cause left unrecorded, the release reason and the lifecycle wording corrected, in 5088211)
- Evidence: checker: PASS with the banned-words variable set to the 191 name tokens from the author list and the documents, with exactly two R12 warnings for the cited all-digit run identifier 28716809559 (accepted by controller ruling under DEC-011 of the standard), and the same by the controller at 5088211; all five cited hashes resolve with the dates and subjects recorded; the GitHub Actions run 28716809559 (2026-07-04, conclusion failure, Windows arm64 job) and the sibling repository's submodule pin were confirmed; no private host, device, address or account appears in the records; the fix (5088211) was read back by diff: eight lines across STATUS.md, VERIFICATION.md and docs/agent-status/README.md, nothing else; the verification report was returned to the controller and is not a file
- Reviewer and disposition: Fable; disposition: the records are verified as of 5088211; no Codex audit is scheduled for this repository; the two R12 warnings are the cited run identifier and stand by design
- Remaining failures, limitations or untested scenarios: no build or test was run by the rollout; the arm64 failure's cause is unrecorded; the lifecycle word, the fork's upstream intent and the CI fix await the owner's answers in the PR
- Who ran it: a read-only verification subagent on Fable's behalf (the checklist and the checker); Fable (the read of its report and this entry)

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
