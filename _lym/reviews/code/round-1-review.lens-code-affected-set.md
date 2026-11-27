```yaml
lens: code-affected-set
outcome: reported
```

Task: the code-affected-set lens. For each change in the diff, find everything outside the touched lines that the change forces to update.

**Per change, the affected set and whether it is covered:**

- **New exported function `ShoutGreeting(name string) string` (`services/api/greeting.go:13-16`)**
  - Callers: none outside its own test. The only production caller in the package is `main.go:6`, and it calls `Greeting("")`, which the diff leaves alone. Covered: no caller is forced to change.
  - Tests: the diff adds `TestShoutGreeting` (`services/api/greeting_test.go:25-42`). `TestGreeting` is unchanged, and the diff does not touch `Greeting`. Covered.
  - Docs: `README.md` and `services/api/doc.go` describe the package in general terms and list no functions, so neither goes stale. Covered.
  - Import: `strings` was already imported at `greeting.go:3`, so no import change is needed. Covered.
- **Behaviour of `Greeting`:** unchanged. `ShoutGreeting` only reuses it, so none of `Greeting`'s readers are affected.
- **Repository rule documents:** the repository has no `PATTERN.md`, no `pattern/` directory, no checked-in `CLAUDE.md` and no constraints document. `git ls-files` shows only `README.md` and `.claude/settings.json`. `CLAUDE.local.md` and `AGENTS.override.md` are untracked tooling instructions, not code conventions. Nothing applies.
- **Declared PATTERN changes landed:** my directive declares none, so there is nothing to check.
- **Stencil wording:** the diff changes no stencil, so this does not apply.
- **Commit messages and departures:** the range holds one commit, 366b126, titled "services/api: add a ShoutGreeting helper that upper-cases the greeting". It has no body and no `Pattern-Departure:`, `Loosened-Check:` or `Root-Cause:` trailers, and none is needed. It touches only the two files in the diff. Covered.

**Findings:** none.

Tool calls:
1. `git ls-files` filtered for PATTERN, CLAUDE, AGENTS, constraints and `.md` files, plus `services/api/s2-note.txt` and `git show --stat 366b126`. My context had not established whether the repository tracks any rule document, and lacked the commit's file list.
