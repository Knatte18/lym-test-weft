# services/api prints a greeting through a Greeting helper

`codex-greet` · Task · enhancement · running · Code-Burler-Fix

## Wanted

- `services/api` gets its own `go.mod` (module `github.com/Knatte18/lym-test/services/api`, go 1.22) so it builds alone.
- A function `Greeting(name string) string` in `services/api/greeting.go` returns `Hello, <name>!`, and `Hello, world!` for an empty or all-whitespace name.
- `main` prints `Greeting("")` to stdout.
- `services/api/greeting_test.go` covers the named, empty and whitespace cases in one table test.
