# SSH trial: add a ShoutGreeting helper in services/api

`ssh-trial-shout` · Task · enhancement · starting · Open-Window

## Aim (operator, 2026-11-27)

A trial of lym over SSH: this hub's code and weft remotes were switched to git@github.com URLs today.
The change itself is small: add a `ShoutGreeting(name string) string` helper in services/api that returns the greeting upper-cased, with one test.

The trial passes when the run goes from Worktree-Create through landing and teardown with every push, fetch and ls-remote over SSH and no stop from transport.
The change description names any step that failed over SSH, with its error.
