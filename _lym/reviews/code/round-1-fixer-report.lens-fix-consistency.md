```yaml
lens: fix-consistency
outcome: reported
```

no findings

The change touches one file, `services/api/greeting_test.go`. The `description` field is used in every row and in `t.Run`, and the `name` field still feeds `Greeting` and the error message. The commit contains no other file. The `services` tree has no sibling table test that would need the same change. The three row names (named, empty, whitespace-only) match the names F1's `fix` key gave.

Tool calls made:
1. `git show --stat HEAD` plus `grep` for `t.Run` and `description` in `services/*.go`. My context lacked the commit's file list and any sibling test files that might share the old naming.
