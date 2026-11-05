# Rename FormatGreeting to ComposeGreeting in services/api

`glyph-rename-format` · Task · enhancement · draft

The exported helper `FormatGreeting` in `services/api/main.go` has a name that under-describes what it does — it composes the whole greeting sentence, not merely formats one. Rename the existing exported function `FormatGreeting` to `ComposeGreeting`, updating its call site in `main()` and every reference in its existing table-driven test. This is a PURE RENAME task: no new behavior, no new symbols beyond the renamed one, no signature change. Preserve git history with surgical edits (identifier retargeting only).