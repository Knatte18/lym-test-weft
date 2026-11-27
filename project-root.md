# P0 Root: entries under no project

Rendered 2026-11-27 15:48 UTC; every age below is as of then.
Under: [Board](README.md).

Owner `neve`

Autonomy _off_ (hub-wide) · PR setting **off**

Tasks are grouped by dependency layer and notes by type.
An entry waits only on the open entries it names under After, so the entries in one layer can run in parallel.

## Running (1)

| # | Task | Slug | Recipe | At | Owner | Age<br>Revised | Labels |
| --- | --- | --- | --- | --- | --- | --- | --- |
| T5 | **SSH trial: add a ShoutGreeting helper in services/api** | [`ssh-trial-shout`](design-ssh-trial-shout.md) | darn · light | starting · Open-Window | neve | 0m<br>0m |  |

## Draft (4)

| # | Task | Slug | Recipe | After | Age<br>Revised | Labels |
| --- | --- | --- | --- | --- | --- | --- |
| T1 | `draft` **Add and rename a greeting helper in services/api**<br>• Add a small greeting helper, call it from main, then rename it to a clearer name. | [`glyph-demo-greet`](design-glyph-demo-greet.md) | darn |  |  |  |
| T2 | `draft` **Rename FormatGreeting to ComposeGreeting in services/api**<br>• Pure rename of an existing exported helper to a clearer name | [`glyph-rename-format`](design-glyph-rename-format.md) | darn |  |  |  |
| T3 | `draft` **Add a farewell path alongside ComposeGreeting in services/api**<br>• Extract a defaultName helper, add ComposeFarewell, and cover it with a table-driven test. | [`r4-crash-hub`](design-r4-crash-hub.md) | darn |  |  |  |
| T4 | `draft` **Add a ComposeGreeting helper with default-name handling in services/api**<br>• Extend the FormatGreeting helper in services/api with default-name handling and a unit test. | [`dummy-r2-greet`](design-dummy-r2-greet.md) | darn |  |  |  |
