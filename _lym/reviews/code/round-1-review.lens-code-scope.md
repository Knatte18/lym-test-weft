```yaml
lens: code-scope
outcome: reported
```

Task: the code-scope lens, which traces each change in the diff to the goal points of the board entry.

**Decisions** (the decision record alone is the answer key; it has no `Added after Discussion` entries, so the goal points come from the board entry's `## Goal`, `_lym/discussion/decision-record.md:3-11`):
- G1: add a `ShoutGreeting(name string) string` helper in services/api that returns the greeting upper-cased (`decision-record.md:7`).
- G2: add one test for it (`decision-record.md:7`).
- G3: the run goes from Worktree-Create through landing and teardown over SSH with no stop from transport (`decision-record.md:9`). This is about how the run goes, so no diff hunk can build it.
- G4: the change description names any step that failed over SSH, with its error (`decision-record.md:10`). This belongs to the change description, not the committed diff.

**Per change:**
- C1, `services/api/greeting.go` hunk @@ -9,3 +9,8 @@: adds `ShoutGreeting` with its doc comment, as `strings.ToUpper(Greeting(name))` (diff lines 9-13). Traces to G1.
- C2, `services/api/greeting_test.go` hunk @@ -21,3 +21,22 @@: adds `TestShoutGreeting`, one table-driven test (diff lines 22-40). Traces to G2.

**Per decision:**
- G1 is built by C1.
- G2 is built by C2.
- G3 is built by no change, and none is due: the goal point is about the run's process, not a code change.
- G4 is built by no hunk, and none is due. The change description carries it in its `## SSH transport` section (`_lym/landing/summary.md:13-16`). Whether that claim is borne out is outside this lens.

**Findings:** none. Every hunk traces to a goal point, and every goal point a diff can build is built. The diff makes no change that the board entry does not license.

Tool calls: none; my context already held everything this lens needed.
