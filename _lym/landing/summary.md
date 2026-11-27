# services/api: add a ShoutGreeting helper

`ShoutGreeting(name string) string` returns the greeting `Greeting` builds for `name`, upper-cased:
`ShoutGreeting("Ada")` is `HELLO, ADA!`, and an empty or whitespace-only name falls back to `HELLO, WORLD!`.
It reuses `Greeting` rather than repeating its default-name rule.

`TestShoutGreeting` pins a named case and the empty-name fallback.

## Design decisions

- Upper-casing uses `strings.ToUpper`, which maps non-ASCII letters by Unicode rules.

## SSH transport

The repository's remotes use `git@github.com` SSH URLs.
No fetch, push or ls-remote failed over SSH before this description was written.

## Merge danger

**Door:** two-way
**Blast radius:** services/api
