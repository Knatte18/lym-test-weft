---
round: 1
ledger:
  - key: subtest-names-not-behaviour
    rounds: [1]
    status: open
    class: consistency
    severity: NIT
    fix: mechanical
---

Round 1 raised F1, a NIT: the table's input field doubles as the `t.Run` name in `services/api/greeting_test.go`.
The review's fix text names the exact change, so the fix is mechanical.
No other findings and no earlier ledger.
