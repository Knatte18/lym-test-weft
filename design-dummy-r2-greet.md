# Add a ComposeGreeting helper with default-name handling in services/api

`dummy-r2-greet` · Task · enhancement · draft

## Background

services/api currently exposes a greeting helper used by main. We want callers to be able to pass an empty name and still get a friendly greeting.

## What to do

- Extend the FormatGreeting helper in services/api so an empty name falls back to a default name ("friend").
- Keep the exported surface small: one exported function returning a greeting string.
- Add a table-driven unit test covering the empty-name fallback and an ordinary name.

## Acceptance

- go build ./... and go test ./... pass in the worktree.
- The helper is called from main.go so the package has a real consumer.