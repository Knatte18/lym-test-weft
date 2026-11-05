# Add a farewell path alongside ComposeGreeting in services/api

`r4-crash-hub` · Task · enhancement · draft

`services/api/main.go` currently exposes `ComposeGreeting(name string) string`, which returns `Hello, <name>!` and defaults an empty name to `world`.

Add a parallel farewell path, in three independently-committable steps, each of which must compile and pass `go test ./...` on its own:

1. Add a new unexported helper `defaultName(name string) string` in `services/api/main.go` that returns `world` when `name` is empty and `name` otherwise, and change `ComposeGreeting` to call it instead of inlining the empty check.
2. Add a new exported `ComposeFarewell(name string) string` in `services/api/main.go` that returns `Goodbye, <name>!` and uses the same `defaultName` helper.
3. Extend `services/api/main_test.go` with a table-driven `TestComposeFarewell` covering the same three cases the existing `TestComposeGreeting` covers, and update `main()` to print both the greeting and the farewell.

No other files change. No new packages, no new files beyond what already exists. Keep every step compiling and independently committable.