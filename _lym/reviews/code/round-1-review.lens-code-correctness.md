```yaml
lens: code-correctness
outcome: reported
```

Task: code-correctness lens on `ShoutGreeting`, the one function the diff adds.

Cases traced:
- `ShoutGreeting`, named input `"Ada"`: `Greeting("Ada")` gives `"Hello, Ada!"`, and `strings.ToUpper` turns it into `"HELLO, ADA!"`. Correct.
- `ShoutGreeting`, empty input `""`: in `Greeting`, `strings.TrimSpace("")` is `""`, so name becomes `"world"`. It returns `"Hello, world!"`, which `ToUpper` turns into `"HELLO, WORLD!"`. Correct.
- `ShoutGreeting`, whitespace-only input `" \t\n"`: `TrimSpace` gives `""`, so name becomes `"world"`, and the result is `"HELLO, WORLD!"`. Correct, and it matches the doc comment at `services/api/greeting.go:13`.
- `ShoutGreeting`, non-ASCII input `"ß"`: `Greeting` gives `"Hello, ß!"`. `ToUpper` maps letters one rune at a time, so `ß`, which has no single-rune upper case, stays `ß` and the result is `"HELLO, ß!"`. That is the documented behaviour of `strings.ToUpper` and is not a wrong result for "upper-cased".
- `ShoutGreeting`, padded input `" Ada "`: the result is `"HELLO,  ADA !"`. The padding comes from `Greeting`'s existing behaviour, which the diff doesn't change, and the upper-casing step is correct.
- Error and failure paths: none. `Greeting` and `strings.ToUpper` cannot fail or return an error, and the function keeps no state.

Findings: none.

Tool calls: none; everything I traced was already in context (`services/api/greeting.go:5-16`).
