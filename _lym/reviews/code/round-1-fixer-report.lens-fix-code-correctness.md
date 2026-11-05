```yaml
lens: fix-code-correctness
outcome: reported
```

Task: check the correctness of the F1 change to `services/api/greeting_test.go` (subtest names).

The fix only changed the test table. It added a `description` field and passes it to `t.Run`. No function signature or production code changed, so no caller can break.

Walk-through of each row, from the gate output in context:
- `{description: "named", name: "Ada"}` runs as `TestGreeting/named`, and `Greeting("Ada")` is checked against `Hello, Ada!`. It passed.
- `{description: "empty", name: ""}` runs as `TestGreeting/empty`, and `Greeting("")` is checked against `Hello, world!`. It passed.
- `{description: "whitespace-only", name: " \t\n"}` runs as `TestGreeting/whitespace-only`, and `Greeting` is checked against `Hello, world!`. It passed.

The three subtest names are unique and readable. The loop variable `test` is read inside the closure, which is safe because `t.Run` runs the subtest synchronously (and Go 1.22 scopes the variable per iteration anyway). The `Errorf` message still prints the input with `%q`, so a failing row is still identified by its input.

The fix adds no new test, so there is no "fails with the defect in place" check to make. The existing assertions are unchanged, and the finding was a naming NIT, not a coverage gap.

no findings

Further tool calls: none. My context already held the changed test file and the gate output.
