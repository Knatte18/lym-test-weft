# Round 1 fixer-report

## Changes

- F1 (NIT): fixed as proposed, commit `89f0e67`.
  In `services/api/greeting_test.go` the table struct gained a `description` field, with rows `named`, `empty` and `whitespace-only`, and `t.Run` takes `test.description`.
  `lym gate test .` from `services/api` passes with subtests `TestGreeting/named`, `TestGreeting/empty` and `TestGreeting/whitespace-only`.

## Self-check

- fix-code-correctness: no findings.
- fix-consistency: no findings.
- fix-proposal: no findings.
- fix-affected-set: no findings.

## Disputed

None.

## Deferred

None.
