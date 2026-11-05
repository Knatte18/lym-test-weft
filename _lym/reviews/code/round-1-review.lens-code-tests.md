```yaml
lens: code-tests
outcome: reported
```

Task: code-tests lens. For each behaviour the diff adds or changes, name the test row that pins it, or none.

**Per-behaviour list**

- **`Greeting("Ada")` returns `Hello, Ada!`:** pinned by the `Ada` row in `TestGreeting` (`services/api/greeting_test.go:11`).
- **`Greeting("")` returns `Hello, world!`:** pinned by the empty-name row (`greeting_test.go:12`).
- **`Greeting(" \t\n")` returns `Hello, world!`:** pinned by the whitespace row (`greeting_test.go:13`). It breaks if `strings.TrimSpace` is dropped.
- **Surrounding whitespace on a non-empty name (for example `" Ada "`):** no row. The code returns `Hello,  Ada !` with the whitespace kept. The entry's Wanted text is silent on trimming, so I treat this as unspecified and not a gap.
- **`main` prints `Greeting("")` to stdout:** no test. `main.go:5-7` has no row. Wanted bullet 3 asks for this output. `main` is a one-line wrapper, and the rubric's test-economy rule would reject a per-helper or subprocess test here. The `Greeting("")` row (`greeting_test.go:12`) covers the string it prints. The remaining untested part is only the `fmt.Println` call and its stdout destination. I found it correct by reading and by the `go run` output in the manifest, so I do not raise a finding.
- **`go.mod` module path and go directive:** no test, and none is warranted. The `go vet`, `go test` and `go run` runs in the manifest compiled and passed in the nested module. A gate decides this, so it is not a test finding.
- **`doc.go` package comment:** static prose, so it is exempt.

**Test-quality checks**

- **One table test:** `greeting_test.go:6` holds a single table-driven test for the three Wanted cases, as Wanted bullet 4 asks. There are no redundant or per-helper tests.
- **Subtest names:** the names are `Ada`, an empty string and `" \t\n"`. `t.Run` rewrites the empty name to `#00` and the whitespace name to `_____`. Both are unique, so the subtests are distinguishable, but they are unreadable. Names such as `named`, `empty` and `whitespace-only` would read better. This is a readability NIT at most; no assertion is lost. The test-naming rule asks names to describe behaviour, and these do not.
- **Assertions:** each row asserts exact equality, and the failure message prints input, got and want with `%q`. It is deterministic and isolated, with no shared state.

**Findings**

1. NIT, class `consistency`, `services/api/greeting_test.go:12-17`. The table field `name` is both the input and the `t.Run` subtest name, so the empty and whitespace-only rows run as `#00` and `_____`. Fix: add a separate `description` field to the table and use it as the subtest name. Evidence: `greeting_test.go:8-13` and `:16`.

No other lens-owned findings.

**Tool calls:** none. The manifest already held every file and the diff.
