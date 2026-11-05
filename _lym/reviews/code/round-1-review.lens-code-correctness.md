```yaml
lens: code-correctness
outcome: reported
```

Task: code-correctness lens review of the `services/api` diff (range `e21d5d5..HEAD`).

**List: function or branch, case ran, result**

- `Greeting`, `name = "Ada"`: `TrimSpace` returns `"Ada"`, which is not empty, so the default is skipped. It returns `"Hello, Ada!"`. Correct.
- `Greeting`, `name = ""`: `TrimSpace` returns `""`, so `name` becomes `"world"`. It returns `"Hello, world!"`. Correct.
- `Greeting`, `name = " \t\n"`: `TrimSpace` strips all of it to `""`, so `name` becomes `"world"`. It returns `"Hello, world!"`. Correct.
- `Greeting`, `name = " Ada "`: `TrimSpace` returns `"Ada"`, which is not empty, so the original `name` is kept untrimmed. It returns `"Hello,  Ada !"`, with the padding preserved. This matches Wanted literally, because `Hello, &lt;name&gt;!` does not ask for trimming. Correct as specified, and not a defect.
- `Greeting`, a Unicode-whitespace name such as `" "`: `strings.TrimSpace` uses `unicode.IsSpace`, which includes U+00A0, so it takes the default. Correct.
- `main`: `fmt.Println(Greeting(""))` prints `Hello, world!` plus a newline to stdout. The handler's earlier `go -C services/api run .` printed exactly that. Correct.
- `main.go`, dropped `Dummy subpath fixture` comment: no code path is affected. The handler's grep found no reference to the comment, and `README.md` refers to the `services/api/` subpath, which still exists. Correct.
- `go.mod`: module path and `go 1.22` match Wanted exactly. `go vet` and `go test` ran clean in the nested module (handler's run). There is no root `go.mod` or `go.work`, so there is no conflict. Correct.
- `TestGreeting`, the three rows: each row asserts the exact string, and `Greeting(%q)` in the failure message makes failures readable. The subtest names are `"Ada"`, `""` (go test renders it as `#00`) and `" \t\n"` (rendered as `_____`). They are distinct and valid, so there is no collision or panic. Correct.
- Loop variable capture in `t.Run`: the closure runs synchronously and does not call `t.Parallel`, and the `go 1.22` per-iteration loop variable semantics apply anyway. Correct.

**Findings:** none.

**Tool calls:** none. Everything needed was already in context from the diff and the handler's build output.
