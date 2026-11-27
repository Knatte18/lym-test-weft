---
verdict: APPROVED
findings:
  - id: F1
    severity: LOW
    class: design
    origin: lens:code-tests
    location: services/api/greeting_test.go#TestShoutGreeting
    summary: TestShoutGreeting has no whitespace-only row, so nothing pins the whitespace fallback the ShoutGreeting doc comment promises.
    fix: "In services/api/greeting_test.go, add the row {description: \"whitespace-only\", name: \" \\t\\n\", want: \"HELLO, WORLD!\"} to the tests table of TestShoutGreeting, after the \"empty\" row."
---

### [LOW] ShoutGreeting's whitespace-only fallback is untested

**Location:** `services/api/greeting_test.go#TestShoutGreeting`

**Issue:** The doc comment at `services/api/greeting.go:13` promises that `ShoutGreeting` uses "world" when name is empty or whitespace, and `_lym/landing/summary.md:4` makes the same claim.
`TestShoutGreeting` has a named row and an empty row only, at `services/api/greeting_test.go:31-32`.
If `ShoutGreeting` stopped falling back for a whitespace-only name, both rows would still pass.
`TestGreeting/whitespace-only` covers `Greeting` alone, not the public `ShoutGreeting` contract.
Adding the row keeps the single test the board entry asks for.

## Holistic review

- The fasit asks for a `ShoutGreeting(name string) string` helper in services/api that returns the greeting upper-cased, plus one test.
  `services/api/greeting.go:14-16` returns `strings.ToUpper(Greeting(name))`, so the default-name path goes through `Greeting` and gives `HELLO, WORLD!`.
- `TestShoutGreeting` asserts literal expected values, so it is not tautological.
  It exercises `ShoutGreeting`, not `Greeting`, so it does not duplicate `TestGreeting`.
- `_lym/landing/summary.md`: each claim about the code matches the diff.
  Its statement that `TestShoutGreeting` pins a named case and the empty-name fallback is accurate.
  Its whitespace-only fallback claim describes the behaviour correctly; the gap is in the test coverage, which F1 records.
  The SSH transport section says no fetch, push or ls-remote failed over SSH before the description was written.
  The board entry asks the description to name any failed step with its error, and this answers that.
  Nothing in the diff or the record contradicts it.
  The description names no tooling.
- Merge danger: the call is `two-way`, with a blast radius of services/api.
  The diff adds one exported function and one test in a `main` package, changes no record or board format and no config meaning, deletes no data and pushes nothing outward.
  The call and the radius match what the diff can break.
- The range has one commit, 366b126, and it carries no trailers.
  None is needed: the change loosens no check and fixes no bug.
- The repository has no constraints document, PATTERN.md or pattern/ directory, so no repository rule or declared PATTERN change applies.
- `go test` was not run here, because the verify gate owns build and test results.
  The code-correctness lens traced the named, empty, whitespace-only, padded and non-ASCII inputs by hand and found them correct.

## Rejected

- None of the lens findings were rejected.
  The code-correctness, code-affected-set and code-scope lenses found nothing.
