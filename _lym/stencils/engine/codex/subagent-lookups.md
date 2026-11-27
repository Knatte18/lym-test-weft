<!-- This is the Codex engine's copy of the subagent-lookups engine block:
     how a writer sends its independent lookups to fresh subagents in one batch.
     A stencil pulls it in on lines of their own, after the lookups are listed, with {{template "engine-subagent-lookups"}}.
     internal/stencilstore reads it for the launch's engine.
     It declares no marker: each fresh subagent runs on the session's own model.
lym-stencil: sha256=7d0f6c1afc848dba834846c09ff6fba933bf6a82f0ac47d285de76b19ca81eae build=2bc62d626810d8eb25759e08749fa2a1a411e4bc time=2026-11-27T15:03:55Z -->
Send the independent ones as one batch to fresh subagents, each spawned with `spawn_agent` and `fork_turns: "none"`, all spawned together, then wait for every one with `wait_agent`.
Give each `spawn_agent` call the `reasoning_effort` that the subagent passage of your developer instructions names, and leave its `model` unset.
