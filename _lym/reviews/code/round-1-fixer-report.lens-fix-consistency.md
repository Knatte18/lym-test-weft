```yaml
lens: fix-consistency
outcome: reported
```

Task: check that the F1 change set (one `whitespace-only` row in `TestShoutGreeting`) agrees with its surroundings.

**LOW** — changed text: the row `{description: "whitespace-only", name: " \t\n", want: "HELLO, WORLD!"}` in `services/api/greeting_test.go`, `TestShoutGreeting`.

Summary: the landing description still lists the test's coverage as it was before the row was added.

Evidence: `_lym/landing/summary.md` says "`TestShoutGreeting` pins a named case and the empty-name fallback." The test now also pins the whitespace-only fallback. The same file's behaviour sentence ("an empty or whitespace-only name falls back to `HELLO, WORLD!`") is still correct. The path is under `_lym`, so no git command may be run against it. Whether the fixer's write surface allows editing the file is for the fixer to judge.

The other surroundings agree. The new row matches the `Greeting`/`ShoutGreeting` doc comments and the sibling `whitespace-only` row in `TestGreeting`, using the same description and input. A search of the `.md` and `.go` files, excluding `.lym` and `reviews`, showed no other mention of `ShoutGreeting`'s test coverage.

Tool calls:
1. One Bash call that read `_lym/landing/summary.md` and searched for `ShoutGreeting`. My context held only the review's account of the summary, not the file or the search.
