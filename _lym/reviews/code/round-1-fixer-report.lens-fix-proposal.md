```yaml
lens: fix-proposal
outcome: reported
```

Task: challenge the F1 proposal (add a `description` field, name subtests from it) in `services/api/greeting_test.go`.

Findings: no findings.

Challenge cases I built:
- **Name collision:** the three descriptions (`named`, `empty`, `whitespace-only`) are unique, so `t.Run` adds no `#01` suffixes.
- **Special characters:** none of the names has a space, so `go test -run` filters work without Go's underscore rewriting. `whitespace-only` keeps its hyphen.
- **Loop-variable capture:** the closure reads `test.description` and `test.name` inside a synchronous `t.Run` with no `t.Parallel()`. The `go 1.22` module also gives each iteration its own variable, so capture is not a problem.
- **Unused field:** `name` is still the input to `Greeting` and is still printed in the `%q` failure message, so nothing became dead.
- **Gate result:** the gate run shows all three subtests as `PASS` under the new names, so the rename broke nothing.

Tool calls made: none. My context already held the changed file and the gate output.
