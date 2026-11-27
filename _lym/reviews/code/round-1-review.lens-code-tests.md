```yaml
lens: code-tests
outcome: reported
```

Task: code-tests lens. For each behaviour the diff adds, find the test row that would fail if the behaviour broke.

Behaviours and the tests that pin them:
- `ShoutGreeting` upper-cases the greeting for a non-empty name: pinned by `TestShoutGreeting/named` (`services/api/greeting_test.go:31`), whose expected value is the literal `"HELLO, ADA!"`.
- `ShoutGreeting` falls back to `world` for an empty name: pinned by `TestShoutGreeting/empty` (`services/api/greeting_test.go:32`), whose expected value is the literal `"HELLO, WORLD!"`.
- `ShoutGreeting` falls back to `world` for a whitespace-only name, as its doc comment states (`services/api/greeting.go:13`): no test pins it.
  `TestGreeting/whitespace-only` (`services/api/greeting_test.go:13`) pins this for `Greeting` only.
  Suppose `ShoutGreeting` were rewritten to check only `name == ""` before upper-casing. Both `TestShoutGreeting` rows would still pass.

Findings:

1. LOW · design · `services/api/greeting_test.go:30-33`
   - Summary: `TestShoutGreeting` has no whitespace-only row, so nothing pins the whitespace fallback that `ShoutGreeting`'s doc comment promises.
   - Fix: add a row `{description: "whitespace-only", name: " \t\n", want: "HELLO, WORLD!"}`.
   - Evidence: `services/api/greeting.go:13` (the doc comment's claim) and `services/api/greeting_test.go:31-32` (the test has only the named and empty rows).

Checked and found no problem:
- Neither row is tautological, because both expected values are literals.
- Neither row duplicates `TestGreeting`, because each one exercises `ShoutGreeting`.

Tool calls: none.
