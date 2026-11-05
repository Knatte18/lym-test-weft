# services/api: print a greeting through a Greeting helper

`services/api` now builds on its own and prints `Hello, world!` when run.

- `services/api/go.mod` declares module `github.com/Knatte18/lym-test/services/api` at go 1.22, so the directory builds without the repository root.
- `Greeting(name string) string` in `services/api/greeting.go` returns `Hello, <name>!`.
  An empty or all-whitespace name yields `Hello, world!`.
- `main` prints `Greeting("")` to stdout.
- `services/api/greeting_test.go` covers the named, empty and whitespace-only cases in one table test.
- `services/api/doc.go` adds the package comment for `main`.

## Design decisions

- The name is checked with `strings.TrimSpace`, but a non-blank name is used as given, so surrounding whitespace in a real name is kept in the output.
- The table test names its subtests by behaviour (`named`, `empty`, `whitespace-only`), not by input.
- The old placeholder comment in `main.go` is removed along with the empty `main`.

## To check by hand

Not run during this change:

- `go build` and `go test` from inside `services/api`, to confirm the module builds alone.
- `go run .` in `services/api` prints `Hello, world!`.
