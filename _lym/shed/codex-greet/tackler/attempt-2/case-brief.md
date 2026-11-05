# Case brief: Darn-Write gate failed three times on uncommitted paths

## Question

Why did the Darn-Write writer (engine codex, trace 00e17e0c8c0a5a9b, strand bdd8e9263f74f2d25107d92248b1bbfb) end three turns without committing five paths in the worktree, and will a fresh spawn on the same worktree commit them?

## Facts

- The stop is `blocked` at producer Darn-Write, reason "gate did not pass after 3 attempts": `_lym/shed/codex-greet/drive-reports/drive-envelope-20261105-101631-2ec6.json`, line 1.
- The gate re-prompted three times with the same finding, at 10:15:17, 10:15:47 and 10:16:12: `.lym/shed/codex-greet/steps/00e17e0c8c0a5a9b.trace.log`, lines 17 to 19.
- The finding names five paths: `services/api/main.go` (modified), `services/api/doc.go`, `services/api/go.mod`, `services/api/greeting.go` and `services/api/greeting_test.go` (untracked). It asks the writer to commit each one that belongs to the change, or delete it: `.lym/shed/codex-greet/gate-findings/Darn-Write.md`, lines 1 to 2.
- The worktree matches the finding now: `git status --short` lists the same five paths, and HEAD is `e21d5d5` ("Rename lyx to lym"), so the writer made no commit: `.lym/logs/trace-20261105T091113Z-00e17e0c8c0a5a9b-3416920.log`, lines 16 to 19 and line 30 (`shed: step done`).
- `git check-ignore` returns no rule for `services/api/go.mod` or `services/api/greeting.go`, so no ignore rule hides them.
- The writer's run dir `.lym/shuttle/44c8b5242d6e0321b59ca7cdd28aaff5` is gone (`cleanedUp=true`, trace line 21), so the writer's own transcript and any commit error it saw are not available.
- The writer's session ran to `idle-done` after each turn, so it did not hang: trace line 20.

## Ruled out

- A tier or gate-config fault: the stop shows `gate=clean`, and the only finding is the uncommitted paths. The `tier0` stop in attempt-1 (trace db1758f3f1274730) is a different stop.
- A gitignore or path-scope fault: `check-ignore` finds no rule.
- A run that never started: the writer ran for about an hour (trace line 15 to 21) and produced the files.
- A plain re-launch as the fix: the way forward in the envelope says `lym loom resume` gives Darn-Write a fresh budget, but three identical failures give no evidence that a fresh budget changes the writer's behaviour.

## Hypothesis (unverified)

The writer's `git commit` fails silently, for example on a commit hook or an identity problem, or the writer believes the five paths are out of scope and ends the turn without committing. Either would explain three identical re-prompts. A check of the writer's own transcript or a manual commit dry run would settle which.
