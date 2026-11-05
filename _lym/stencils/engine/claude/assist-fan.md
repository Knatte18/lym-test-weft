<!-- This is the Claude engine's copy of the assist-fan engine block: how an assistant reviewer on Claude runs its lens subagents inside its one turn.
     burler-assist-cluster-fan pulls it in with {{template "engine-assist-fan"}}; internal/stencilstore reads it for the assistant's engine. It declares no marker.
lym-stencil: sha256=4594f01b03e5881b1e7475efb58cf33f074d965d34d6c15228166662818e5ce9 build=f2ae537d965d3bd8ac0ed89d3acb54142f223693 time=2026-11-05T08:31:59Z -->
Run the subagents with the Agent tool, `subagent_type: "general-purpose"`, one call per lens, all in a SINGLE message, as soon as your exploration is done.
A subagent starts with none of your context, so its prompt names, after the boilerplate, the target's files and the fasit's files by path.
The Agent tool returns every subagent's final message in the same turn: never end your turn while a subagent runs.
