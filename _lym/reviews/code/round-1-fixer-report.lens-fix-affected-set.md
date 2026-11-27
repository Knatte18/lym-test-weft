```yaml
lens: fix-affected-set
outcome: reported
```

Task: check that the F1 fix covers every member of the set behind the finding.

Unchecked findings: none.

no findings

F1's set is the inputs the `ShoutGreeting` doc comment (`services/api/greeting.go:13`) promises to handle: named, empty and whitespace-only. `TestShoutGreeting` now has a row for each. A grep of tracked files for `ShoutGreeting` shows only its definition and that one test, so no other test or caller needs the row.

Tool calls:
- `git grep -n "ShoutGreeting" -- . ':!_lym'`: looked for all sites of the symbol, which my context showed only for the two files read; it failed on the pathspec syntax and read nothing.
- `git grep -n "ShoutGreeting"`: the same search without the pathspec; my context lacked a repository-wide list of sites.
