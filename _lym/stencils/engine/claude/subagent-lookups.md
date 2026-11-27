<!-- This is the Claude engine's copy of the subagent-lookups engine block:
     how a writer sends its independent lookups to fresh subagents in one batch.
     A stencil pulls it in on lines of their own, after the lookups are listed, with {{template "engine-subagent-lookups"}}.
     internal/stencilstore reads it for the launch's engine.
     It declares one required marker, {{.subagent_model}}, the model each fresh subagent runs on.
lym-stencil: sha256=e9dd0b6413168d71a4a8abebbe6fc95a2f9ec7593ed636fafe21508f7c49b868 build=2bc62d626810d8eb25759e08749fa2a1a411e4bc time=2026-11-27T15:03:55Z -->
Send the independent ones as one batch to fresh subagents through the Agent tool, each with `subagent_type: "general-purpose"` and `model: "{{.subagent_model}}"`, all launched together in one message.
Give each Agent call the `effort` that the subagent passage of your system prompt names.
