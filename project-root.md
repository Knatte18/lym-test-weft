# P0 Root: entries under no project

Rendered 2026-11-05 12:10 UTC; every age below is as of then.
Under: [Board](README.md).

Owner `neve`

Tasks are grouped by dependency layer and notes by type.
An entry waits only on the open entries it names under After, so the entries in one layer can run in parallel.

## Tasks (5)

Concrete and claimable; only a task can run.

### Running (1)

Held by a run; its scope is locked until the run ends.

| # | Task | Slug | Recipe | At | Owner | Age<br>Revised | Labels |
| --- | --- | --- | --- | --- | --- | --- | --- |
| T5 | **services/api prints a greeting through a Greeting helper**<br>• Add go.mod for services/api and a Greeting helper that main prints | [`codex-greet`](design-codex-greet.md) | darn · light | Drift-Recheck | neve | 3h<br>3h |  |

### Ready (0)

Waits on nothing open; can start now.

_None._

### Draft (4)

Not released; nothing starts it until its status is cleared.

| # | Task | Slug | Recipe | After | Age<br>Revised | Labels |
| --- | --- | --- | --- | --- | --- | --- |
| T1 | `draft` **Add and rename a greeting helper in services/api**<br>• Add a small greeting helper, call it from main, then rename it to a clearer name. | [`glyph-demo-greet`](design-glyph-demo-greet.md) | darn |  |  |  |
| T2 | `draft` **Rename FormatGreeting to ComposeGreeting in services/api**<br>• Pure rename of an existing exported helper to a clearer name | [`glyph-rename-format`](design-glyph-rename-format.md) | darn |  |  |  |
| T3 | `draft` **Add a farewell path alongside ComposeGreeting in services/api**<br>• Extract a defaultName helper, add ComposeFarewell, and cover it with a table-driven test. | [`r4-crash-hub`](design-r4-crash-hub.md) | darn |  |  |  |
| T4 | `draft` **Add a ComposeGreeting helper with default-name handling in services/api**<br>• Extend the FormatGreeting helper in services/api with default-name handling and a unit test. | [`dummy-r2-greet`](design-dummy-r2-greet.md) | darn |  |  |  |

## Notes (0)

Not tasks: ideas and observations, merged into a task when one is promoted.
