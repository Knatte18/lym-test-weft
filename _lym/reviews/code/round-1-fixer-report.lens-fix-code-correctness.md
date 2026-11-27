```yaml
lens: fix-code-correctness
outcome: reported
```

Task: fix-code-correctness check of the one added test row, `{whitespace-only, " \t\n", "HELLO, WORLD!"}` in `TestShoutGreeting`.

no findings

Trace: `ShoutGreeting(" \t\n")` calls `Greeting`, where `strings.TrimSpace` returns `""`, so the name becomes "world" and the result is "Hello, world!". `strings.ToUpper` turns that into "HELLO, WORLD!", which matches `want`. Neither call can return an error.

With the fallback gone, the result would be "HELLO,  \t\n!" and the row would fail. The same holds if the check were weakened to `name == ""`. The fix changed no signature or behaviour, so no caller is affected. The gate output shows `TestShoutGreeting/whitespace-only` ran and passed.

Further tool calls: none.
