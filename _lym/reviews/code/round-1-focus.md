---
round: 1
focus:
  - "services/api/greeting.go and greeting_test.go: does ShoutGreeting return the upper-cased greeting the amended board entry asks for, including through Greeting's default-name path, and does the added test check that behaviour against independent expected values without duplicating TestGreeting's coverage?"
  - "_lym/landing/summary.md: does the diff, and what the writer could know when writing, bear out each claim, including the empty or whitespace-only fallback, what TestShoutGreeting pins, and the SSH transport section against the board entry's request to name any step that failed over SSH with its error?"
  - "_lym/landing/summary.md `## Merge danger`: do the door and blast radius match what the committed diff can break?"
---

The range holds one commit touching services/api, so the open questions are the helper's behaviour, its test and the change description's claims.
