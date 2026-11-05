```yaml
lens: fix-affected-set
outcome: reported
```

no findings

The finding's premise is the set of `t.Run` sites that name a subtest after its input. One search over `services/api` found a single `t.Run` call, at `greeting_test.go:17`, and the fix covers it. Every row at lines 11–13 carries a `description`, and none is empty or repeated.

- Ran `grep -rn "t.Run\|name:"` over the `.go` files under `services/`. The context held only `greeting_test.go`, so it could not show whether other test files in `services/` have `t.Run` calls.
