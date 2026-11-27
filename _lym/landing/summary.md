# services/api: add a ShoutGreeting helper

Adds `ShoutGreeting(name string) string` to `services/api`, which returns the greeting for `name` upper-cased.
`Greeting` is unchanged, and the diff adds no caller of the new helper outside its test.

The helper upper-cases the result of `Greeting`, so it shares that function's fallback:
an empty or whitespace-only name gives `HELLO, WORLD!`.
`TestShoutGreeting` covers a named, an empty and a whitespace-only input.

The change also serves as a trial of working with the GitHub remotes over SSH (`git@github.com` URLs).
No push, fetch or `ls-remote` is known to have failed over SSH up to the writing of this description.
Steps that come after it, including the merge and cleanup, are not covered by that statement.

## Merge danger

**Door:** two-way
**Blast radius:** api
